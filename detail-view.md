---
layout: module
title: Module 5&#58; Add the Details View
---

In this module, you will add a Details View to view the details of the selected Contact.

Using MVC Scaffolding, we can build out the view based on the Model classes scaffolded based on the Salesforce objects.


- Within the Controller.Details Method, right-click and select **Add View**
  - View name: **Details**
  - Template: **Details**
  - Model: **Contact ([YourProjectName].Models.Salesforce)**
- Click Add
- Replace the contents of the razor file with the following code:
> **Note:** Replace the @model namespace WebApplication1 with the namespace of your project

```html
@model WebApplication1.Models.Salesforce.Contact
@{
    ViewBag.Title = "View";
}
<h2>View</h2>
<div>
    <h4>Contact</h4>
    <hr />
    <dl class="dl-horizontal">
        <dt>
            @Html.DisplayNameFor(model => model.Salutation)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.Salutation)
        </dd>
        <dt>
            @Html.DisplayNameFor(model => model.FirstName)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.FirstName)
        </dd>
        <dt>
            @Html.DisplayNameFor(model => model.LastName)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.LastName)
        </dd>
        <dt>
            @Html.DisplayNameFor(model => model.MailingStreet)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.MailingStreet)
        </dd>
        <dt>
            @Html.DisplayNameFor(model => model.MailingCity)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.MailingCity)
        </dd>
        <dt>
            @Html.DisplayNameFor(model => model.MailingState)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.MailingState)
        </dd>
        <dt>
            @Html.DisplayNameFor(model => model.MailingPostalCode)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.MailingPostalCode)
        </dd>
        <dt>
            @Html.DisplayNameFor(model => model.MailingCountry)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.MailingCountry)
        </dd>
        <dt>
            @Html.DisplayNameFor(model => model.Phone)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.Phone)
        </dd>
        <dt>
            @Html.DisplayNameFor(model => model.Email)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.Email)
        </dd>
    </dl>
</div>
<p>
    @Html.ActionLink("Edit", "Edit", new { id = Model.Id }) |
    @Html.ActionLink("Back to List", "Index")
</p>
```






<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="index-list-view.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="create-apex-controller.html" class="btn btn-default pull-right">Next <i class="glyphicon glyphicon-chevron-right"></i></a>
</div>
</div>
