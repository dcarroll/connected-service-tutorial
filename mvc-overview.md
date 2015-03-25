---
layout: module
title: Module 1&#58; MVC Overview
---

## Creating an MVC app to view, edit and delete Salesforce Contacts

# ASP.net MVC apps follow the Model-View-Controller pattern.

In the following steps, you'll create:

- An MVC Controller to retrieve the Contact object and provide Query, Create, Update and Delete functionality. Within the Controller, we'll validate the connection is authenticated. If not, the user will be redirected to login.
- A Menu in the common Layouts folder for listing your Salesforce Contacts.
- 4 Views using razor syntax for Index, Create, Update and Delete. The Delete View will include a confirmation view as best practices include confirming the user really wanted to perform a destructive action.
- This sample assumes you selected the Contact Salesforce Object in the scaffolding step of the wizard.

<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="index.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="mvc-controller.html" class="btn btn-default pull-right">Next <i class="glyphicon glyphicon-chevron-right"></i></a>
</div>
</div>
