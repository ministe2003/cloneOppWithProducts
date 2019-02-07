# cloneOppWithProducts
Lightning solution to clone opportunity with products

## Overview
Based on the [CloneOpp component by Naval Sharma](https://github.com/sfcure/CloneOpp) - this project extends his excellent work to try and improve and expand it's abilities.

## Salesforce Idea
[Here's a link](https://success.salesforce.com/ideaView?id=0873A000000cMbMQAU) to the Idea for Salesforce to restore this as standard

## Differences from CloneOpp
- In CloneOpp the opportunity is cloned without any input from the user, based on fields which are placed in a fieldset.  There is no way for changes to be made to the opportunity before the clone takes place
   * _This component replicates Salesforce's own Clone behaviour by displaying the opportunity page layout and allowing changes before the clone takes place_
- In CloneOpp, the opportunity product fields are hard coded into the table meaning you can only change the values of Quantity, Sales Price, Date and Description
   * _This component builds the table dynamically using the using lightning:datatable component, and displays whatever fields you decide to add to a fieldset_
- In CloneOpp some errors are suppressed
   * _Some errors are only logged to the console and aren't displayed to the user.  This component uses improved error handling to keep the user informed along the way_

## Usage Instructions
Once the package has been installed and set up, clicking the Clone with Products button will first open a window where you can edit the opportunity before you clone it.  This is to repliace the behaviour of the standard Clone button.  Once the opportunity has been saved the lines will appear in a table.
   - If you press Save without making any changes, the lines will be cloned as they are.
   - If you press Cancel, the lines will not be cloned.  This replicates the standard Clone with Products behaviour in Salesforce Classic.
   - Alternatively you can inline-edit any editable fields or delete any lines you do not want to clone.  When you're finished press Save to clone the lines.
Once the clone has completed you will be redirected to the new opportunity.

## Setup Instructions
1. Install the package by clicking the relevant link for your org, either Sandbox or Production.  It's recommended to test this in your Sandbox first.
2. Add the 'Clone with Products' lightning action to your page layout(s)
3. You will need to update 2 fieldsets to decide which Opportunity Line Item fields to clone, and which to make available for editing before performing the clone:
- Navigate to the Opportunity Product object
   * In classic: Setup | Customize | Opportunities | Opportunity Products | Field Sets
   * In lightning: Setup | Objects and Fields | Object Manager | Opportunity Product | Field Sets
- Select fields to clone
   * Open 'Clone Opportunity Field Set' for editing
   * Add and remove fields to the fieldset which you wish to be included in the clone operation and Save
- Select fields to make editable
   * Open 'Clone Opportunity Editable Field Set' for editing
   * Add and remove fields to the field set which you wish to be made available for editing before the lines are cloned.  Fields included in this field set will be displayed in a table so users can modify the values.  Field Level Security is respected and formula fields added to this field set will be displayed in the table but not editable.

## Packages
This package is only available as an unmanaged package
- Sandbox [installation](https://test.salesforce.com/packaging/installPackage.apexp?p0=04t5B0000006JHl&isdtp=p1)
- Production [installation](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t5B0000006JHl&isdtp=p1)

## Limitations
Relationship fields (lookup and master detail) cannot be added to the 'Clone Opportunity Editable Field Set' or you will receive an error when attempting to clone the lines.  This is due to a limitation in the Lightning:Datatable component.

## Credit
Again, credit must be given to [Naval Sharma](https://github.com/sfcure/CloneOpp) and his CloneOpp component which formed the basis for this project.