# Self Service QuickAdd Package

## What were we trying to solve?

The majority of technical staff at JAMF Software are provisioned multiple OS X and iOS devices for production and testing use. Submission of inventory of these test devices is a requirement of the security policies here. As logging into the over-the-air enrollment page on each these devices can be a chore (some staff manage entire kits of devices), we created an option in Self Service for them to generate an OS X QuickAdd package for inventory purposes.

Only JSS admins have the privileges to create re-usable QuickAdd packages. We wanted to provide this ability without elevating permissions to the JSS, while at the same time taking steps to ensure the inventory of the JSS was properly maintained and devices were correctly assigned as staff used these packages to enroll them.

## What does it do?

The script takes (via a script parameter) a computer invitation generated by IT, and builds a QuickAdd package locally on the user's desktop. The post-install script of this package will also include the username captured from Self Service, so any Macs it is used on will be assigned to the person who generated the package. The built package is revealed in the Finder.

The user can take this package and enroll Macs to the JSS for inventory purposes. If the computer invitation is invalidated or updated, the staff member would re-run the policy to generate a new one. This allows IT to maintain control over the computer invitations, while allowing staff to have access to re-usable QuickAdd packages.

## How to deploy this script in a policy

Upload the script to your JSS and create a policy. You will want to modify some of the variables in the script (the package's 'bundleid' and the 'jssURL') for your organization. You will need to generate the computer invitation that will be used for packages built by this script. Once you have the computer invitation string, paste it into parameter #4 of the policy. This script has been tested against 10.9 and 10.10 clients.

## License

```
Copyright (c) 2015, JAMF Software, LLC. All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are
permitted provided that the following conditions are met:

    * Redistributions of source code must retain the above copyright notice, this
      list of conditions and the following disclaimer.
    * Redistributions in binary form must reproduce the above copyright notice, this
      list of conditions and the following disclaimer in the documentation and/or
      other materials provided with the distribution.
    * Neither the name of the JAMF Software, LLC nor the names of its contributors
      may be used to endorse or promote products derived from this software without
      specific prior written permission.
      
THIS SOFTWARE IS PROVIDED BY JAMF SOFTWARE, LLC "AS IS" AND ANY EXPRESS OR IMPLIED
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY
AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL JAMF SOFTWARE,
LLC BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS
OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED
AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE,
EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```