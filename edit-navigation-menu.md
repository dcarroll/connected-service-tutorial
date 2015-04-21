---
layout: module
title: Module 4&#58; Edit Navigation Menu
---

In this module, you will add new menu item to the sample menu to navigate to a list view of your data.

### Add a Menu Item for Salesforce Contacts

- Open Views\Shared\_Layout.cshtml.
- Within the ```<ul class="nav navbar-nav">``` div, add the last ```<li>``` to your code:


<button id="click2copy" data-clipboard-target="clipdata" data-text-type="html">Copy to Clipboard</button>

```html
<ul class="nav navbar-nav">
    <li>@Html.ActionLink("Home", "Index", "Home")</li>
    <li>@Html.ActionLink("About", "About", "Home")</li>
    <li>@Html.ActionLink("Contact", "Contact", "Home")</li>
    <li>@Html.ActionLink("Salesforce Contacts", "Index", "Contacts")</li> 
</ul>
```



<div style="display: none;" id="clipdata">
<ul class="nav navbar-nav">
    <li>@Html.ActionLink("Home", "Index", "Home")</li>
    <li>@Html.ActionLink("About", "About", "Home")</li>
    <li>@Html.ActionLink("Contact", "Contact", "Home")</li>
    <li>@Html.ActionLink("Salesforce Contacts", "Index", "Contacts")</li> 
</ul>
</div>


<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="mvc-controller.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="index-list-view.html" class="btn btn-default pull-right">Next <i class="glyphicon glyphicon-chevron-right"></i></a>
</div>
</div>
