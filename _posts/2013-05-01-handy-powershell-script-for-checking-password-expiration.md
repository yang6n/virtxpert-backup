---
ID: 782
post_title: >
  Handy PowerShell script for checking
  password expiration
author: Jonathan Frappier
post_date: 2013-05-01 15:01:06
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/handy-powershell-script-for-checking-password-expiration/
published: true
dsq_thread_id:
  - "1295323445"
---
This is not something I wrote, but much like the person who created the script was faced with a question today on how to determine when an AD account password will expire.  I had been using a VB script but it relies on manual input to determine what the password expiration policy is set to, this PowerShell script reads from either the default domain policy or the fine grained password policy to determine this.

Here you can see the results of the script before and after updating the policy from 42 to 120.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/05/pwexpiration.png"><img class="aligncenter size-full wp-image-783" alt="pwexpiration" src="http://www.virtxpert.com/wp-content/uploads/2013/05/pwexpiration.png" width="517" height="258" /></a>

&nbsp;

Link to the script and more information on it can be found <a href="http://blogs.msdn.com/b/adpowershell/archive/2010/08/09/9970198.aspx" target="_blank">here</a>, or the script itself below.  And thanks "Swami" for sharing.

<!--more-->
<pre>function Get-XADUserPasswordExpirationDate() {

    Param ([Parameter(Mandatory=$true,  Position=0,  ValueFromPipeline=$true, HelpMessage="Identity of the Account")]

    [Object] $accountIdentity)

    PROCESS {

        $accountObj = Get-ADUser $accountIdentity -properties PasswordExpired, PasswordNeverExpires, PasswordLastSet

        if ($accountObj.PasswordExpired) {

            echo ("Password of account: " + $accountObj.Name + " already expired!")

        } else { 

            if ($accountObj.PasswordNeverExpires) {

                echo ("Password of account: " + $accountObj.Name + " is set to never expires!")

            } else {

                $passwordSetDate = $accountObj.PasswordLastSet

                if ($passwordSetDate -eq $null) {

                    echo ("Password of account: " + $accountObj.Name + " has never been set!")

                }  else {

                    $maxPasswordAgeTimeSpan = $null

                    $dfl = (get-addomain).DomainMode

                    if ($dfl -ge 3) { 

                        ## Greater than Windows2008 domain functional level

                        $accountFGPP = Get-ADUserResultantPasswordPolicy $accountObj

                        if ($accountFGPP -ne $null) {

                            $maxPasswordAgeTimeSpan = $accountFGPP.MaxPasswordAge

                        } else {

                            $maxPasswordAgeTimeSpan = (Get-ADDefaultDomainPasswordPolicy).MaxPasswordAge

                        }

                    } else {

                        $maxPasswordAgeTimeSpan = (Get-ADDefaultDomainPasswordPolicy).MaxPasswordAge

                    }

                    if ($maxPasswordAgeTimeSpan -eq $null -or $maxPasswordAgeTimeSpan.TotalMilliseconds -eq 0) {

                        echo ("MaxPasswordAge is not set for the domain or is set to zero!")

                    } else {

                        echo ("Password of account: " + $accountObj.Name + " expires on: " + ($passwordSetDate + $maxPasswordAgeTimeSpan))

                    }

                }

            }

        }

    }

}</pre>