---
layout: module
title: Module 5&#58; Add the List View
---

In this module, you will add List View to view the list of Salesforce Contacts.

Using MVC Scaffolding, we can build out the view based on the Model classes scaffolded based on the Salesforce objects.


- Within the Controller.Index Method, right-click and select **Add View**
  - View name: **Index**
  - Template: **List**
  - Model: **Contact ([YourProjectName].Models.Salesforce)**
- Click Add
- Replace the contents of the razor file with the following code:
> **Note:** Replace the @model namespace WebApplication1 with the namespace of your project


<button id="click2copy" data-clipboard-target="clipdata" data-text-type="code">Copy to Clipboard</button>


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
<div style="display: none;" id="clipdata">
@model IEnumerable<span class="kwrd">&lt;</span><span class="html">WebApplication1.Models.Salesforce.Contact</span><span class="kwrd">&gt;</span>
@{
    ViewBag.Title = "Contacts";
}
<span class="kwrd">&lt;</span><span class="html">h2</span><span class="kwrd">&gt;</span>Contacts<span class="kwrd">&lt;/</span><span class="html">h2</span><span class="kwrd">&gt;</span>
<span class="kwrd">&lt;</span><span class="html">p</span><span class="kwrd">&gt;</span>
    @Html.ActionLink("Create New", "Create")
<span class="kwrd">&lt;/</span><span class="html">p</span><span class="kwrd">&gt;</span>
<span class="kwrd">&lt;</span><span class="html">table</span> <span class="attr">class</span><span class="kwrd">="table"</span><span class="kwrd">&gt;</span>
    <span class="kwrd">&lt;</span><span class="html">tr</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">th</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.Salutation)
        <span class="kwrd">&lt;/</span><span class="html">th</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">th</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.FirstName)
        <span class="kwrd">&lt;/</span><span class="html">th</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">th</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.LastName)
        <span class="kwrd">&lt;/</span><span class="html">th</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">th</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.MailingCity)
        <span class="kwrd">&lt;/</span><span class="html">th</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">th</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.MailingState)
        <span class="kwrd">&lt;/</span><span class="html">th</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">th</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.MailingCountry)
        <span class="kwrd">&lt;/</span><span class="html">th</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">th</span><span class="kwrd">&gt;&lt;/</span><span class="html">th</span><span class="kwrd">&gt;</span>
    <span class="kwrd">&lt;/</span><span class="html">tr</span><span class="kwrd">&gt;</span>
    @foreach (var item in Model) {
        <span class="kwrd">&lt;</span><span class="html">tr</span><span class="kwrd">&gt;</span>
            <span class="kwrd">&lt;</span><span class="html">td</span><span class="kwrd">&gt;</span>
                @Html.DisplayFor(modelItem =<span class="kwrd">&gt;</span> item.Salutation)
            <span class="kwrd">&lt;/</span><span class="html">td</span><span class="kwrd">&gt;</span>
            <span class="kwrd">&lt;</span><span class="html">td</span><span class="kwrd">&gt;</span>
                @Html.DisplayFor(modelItem =<span class="kwrd">&gt;</span> item.FirstName)
            <span class="kwrd">&lt;/</span><span class="html">td</span><span class="kwrd">&gt;</span>
            <span class="kwrd">&lt;</span><span class="html">td</span><span class="kwrd">&gt;</span>
                @Html.DisplayFor(modelItem =<span class="kwrd">&gt;</span> item.LastName)
            <span class="kwrd">&lt;/</span><span class="html">td</span><span class="kwrd">&gt;</span>
            <span class="kwrd">&lt;</span><span class="html">td</span><span class="kwrd">&gt;</span>
                @Html.DisplayFor(modelItem =<span class="kwrd">&gt;</span> item.MailingCity)
            <span class="kwrd">&lt;/</span><span class="html">td</span><span class="kwrd">&gt;</span>
            <span class="kwrd">&lt;</span><span class="html">td</span><span class="kwrd">&gt;</span>
                @Html.DisplayFor(modelItem =<span class="kwrd">&gt;</span> item.MailingState)
            <span class="kwrd">&lt;/</span><span class="html">td</span><span class="kwrd">&gt;</span>
            <span class="kwrd">&lt;</span><span class="html">td</span><span class="kwrd">&gt;</span>
                @Html.DisplayFor(modelItem =<span class="kwrd">&gt;</span> item.MailingCountry)
            <span class="kwrd">&lt;/</span><span class="html">td</span><span class="kwrd">&gt;</span>
            <span class="kwrd">&lt;</span><span class="html">td</span><span class="kwrd">&gt;</span>
                @Html.ActionLink("Edit", "Edit", new { id = item.Id }) |
                @Html.ActionLink("Details", "Details", new { id = item.Id }) |
                @Html.ActionLink("Delete", "Delete", new { id = item.Id })
            <span class="kwrd">&lt;/</span><span class="html">td</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;/</span><span class="html">tr</span><span class="kwrd">&gt;</span>
    }
<span class="kwrd">&lt;/</span><span class="html">table</span><span class="kwrd">&gt;</span>
</div>



<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="edit-navigate-menu.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="detail-view.html" class="btn btn-default pull-right">Next <i class="glyphicon glyphicon-chevron-right"></i></a>
</div>
</div>
