---
layout: module
title: Module 7&#58; Add the Delete View
---

In this module, you will add a Delete View to demonstrate how to delete the selected Contact.

Using MVC Scaffolding, we can build out the view based on the Model classes scaffolded based on the Salesforce objects.


- Within the Controller.Delete Method, right-click and select **Add View**
  - View name: **Delete**
  - Template: **Delete**
  - Model: **Contact ([YourProjectName].Models.Salesforce)**
- Click Add
- Replace the contents of the razor file with the following code:
> **Note:** Replace the @model namespace WebApplication1 with the namespace of your project

```html
@model WebApplication1.Models.Salesforce.Contact
@{
    ViewBag.Title = "Delete";
}
<h2>Delete</h2>
<h3>Are you sure you want to delete this?</h3>
<div>
    <h4>Contact</h4>
    <hr />
    <dl class="dl-horizontal">
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
            @Html.DisplayNameFor(model => model.MailingCountry)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.MailingCountry)
        </dd>
    </dl>
    @using (Html.BeginForm()) {
        @Html.AntiForgeryToken()
        <div class="form-actions no-color">
            <input type="submit" value="Delete" class="btn btn-default" /> |
            @Html.ActionLink("Back to List", "Index")
        </div>
    }
</div>
```






<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="edit-view.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="create-view.html" class="btn btn-default pull-right">Next <i class="glyphicon glyphicon-chevron-right"></i></a>
</div>
</div>
