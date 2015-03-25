---
layout: module
title: Module 4&#58; Add the List View
---

In this module, you will add List View to view the list of Salesforce Contacts.

Using MVC Scaffolding, we can build out the view based on the Model classes scaffolded based on the Salesforce objects.

> **Note:** Because we're using a new auth pattern for validating users inline, there are two extra **Partial** views added to the page.  Copying this code will add these views, however as you move past the sample and use the MVC View Scaffolding, be sure to add these partial views if you continue to use the auth pattern in the controllers.

- Within the Controller.Index Method, right-click and select **Add View**
  - View name: **Index**
  - Template: **List**
  - Model: **Contact ([YourProjectName].Models.Salesforce)**
- Click Add
- Replace the contents of the razor file with the following code:
> **Note:** Replace the @model namespace WebApplication1 with the namespace of your project

```html
@model IEnumerable<WebApplication1.Models.Salesforce.Contact>
@{
    ViewBag.Title = "Contacts";
}
<h2>Contacts</h2>
<p>
    @Html.ActionLink("Create New", "Create")
</p>
<table class="table">
    <tr>
        <th>
            @Html.DisplayNameFor(model => model.Salutation)
        </th>
        <th>
            @Html.DisplayNameFor(model => model.FirstName)
        </th>
        <th>
            @Html.DisplayNameFor(model => model.LastName)
        </th>
        <th>
            @Html.DisplayNameFor(model => model.MailingCity)
        </th>
        <th>
            @Html.DisplayNameFor(model => model.MailingState)
        </th>
        <th>
            @Html.DisplayNameFor(model => model.MailingCountry)
        </th>
        <th></th>
    </tr>
    @foreach (var item in Model) {
        <tr>
            <td>
                @Html.DisplayFor(modelItem => item.Salutation)
            </td>
            <td>
                @Html.DisplayFor(modelItem => item.FirstName)
            </td>
            <td>
                @Html.DisplayFor(modelItem => item.LastName)
            </td>
            <td>
                @Html.DisplayFor(modelItem => item.MailingCity)
            </td>
            <td>
                @Html.DisplayFor(modelItem => item.MailingState)
            </td>
            <td>
                @Html.DisplayFor(modelItem => item.MailingCountry)
            </td>
            <td>
                @Html.ActionLink("Edit", "Edit", new { id = item.Id }) |
                @Html.ActionLink("Details", "Details", new { id = item.Id }) |
                @Html.ActionLink("Delete", "Delete", new { id = item.Id })
            </td>
        </tr>
    }
</table>
```






<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="edit-navigate-menu.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="create-apex-controller.html" class="btn btn-default pull-right">Next <i class="glyphicon glyphicon-chevron-right"></i></a>
</div>
</div>
