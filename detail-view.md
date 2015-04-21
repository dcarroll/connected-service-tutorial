---
layout: module
title: Module 6&#58; Add the Details View
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


<button id="click2copy" data-clipboard-target="clipdata" data-text-type="code">Copy to Clipboard</button>



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


<div style="display: none;" id="clipdata">
@model WebApplication1.Models.Salesforce.Contact
@{
    ViewBag.Title = "View";
}
<span class="kwrd">&lt;</span><span class="html">h2</span><span class="kwrd">&gt;</span>View<span class="kwrd">&lt;/</span><span class="html">h2</span><span class="kwrd">&gt;</span>
<span class="kwrd">&lt;</span><span class="html">div</span><span class="kwrd">&gt;</span>
    <span class="kwrd">&lt;</span><span class="html">h4</span><span class="kwrd">&gt;</span>Contact<span class="kwrd">&lt;/</span><span class="html">h4</span><span class="kwrd">&gt;</span>
    <span class="kwrd">&lt;</span><span class="html">hr</span> <span class="kwrd">/&gt;</span>
    <span class="kwrd">&lt;</span><span class="html">dl</span> <span class="attr">class</span><span class="kwrd">="dl-horizontal"</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dt</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.Salutation)
        <span class="kwrd">&lt;/</span><span class="html">dt</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dd</span><span class="kwrd">&gt;</span>
            @Html.DisplayFor(model =<span class="kwrd">&gt;</span> model.Salutation)
        <span class="kwrd">&lt;/</span><span class="html">dd</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dt</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.FirstName)
        <span class="kwrd">&lt;/</span><span class="html">dt</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dd</span><span class="kwrd">&gt;</span>
            @Html.DisplayFor(model =<span class="kwrd">&gt;</span> model.FirstName)
        <span class="kwrd">&lt;/</span><span class="html">dd</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dt</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.LastName)
        <span class="kwrd">&lt;/</span><span class="html">dt</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dd</span><span class="kwrd">&gt;</span>
            @Html.DisplayFor(model =<span class="kwrd">&gt;</span> model.LastName)
        <span class="kwrd">&lt;/</span><span class="html">dd</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dt</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.MailingStreet)
        <span class="kwrd">&lt;/</span><span class="html">dt</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dd</span><span class="kwrd">&gt;</span>
            @Html.DisplayFor(model =<span class="kwrd">&gt;</span> model.MailingStreet)
        <span class="kwrd">&lt;/</span><span class="html">dd</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dt</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.MailingCity)
        <span class="kwrd">&lt;/</span><span class="html">dt</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dd</span><span class="kwrd">&gt;</span>
            @Html.DisplayFor(model =<span class="kwrd">&gt;</span> model.MailingCity)
        <span class="kwrd">&lt;/</span><span class="html">dd</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dt</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.MailingState)
        <span class="kwrd">&lt;/</span><span class="html">dt</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dd</span><span class="kwrd">&gt;</span>
            @Html.DisplayFor(model =<span class="kwrd">&gt;</span> model.MailingState)
        <span class="kwrd">&lt;/</span><span class="html">dd</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dt</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.MailingPostalCode)
        <span class="kwrd">&lt;/</span><span class="html">dt</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dd</span><span class="kwrd">&gt;</span>
            @Html.DisplayFor(model =<span class="kwrd">&gt;</span> model.MailingPostalCode)
        <span class="kwrd">&lt;/</span><span class="html">dd</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dt</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.MailingCountry)
        <span class="kwrd">&lt;/</span><span class="html">dt</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dd</span><span class="kwrd">&gt;</span>
            @Html.DisplayFor(model =<span class="kwrd">&gt;</span> model.MailingCountry)
        <span class="kwrd">&lt;/</span><span class="html">dd</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dt</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.Phone)
        <span class="kwrd">&lt;/</span><span class="html">dt</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dd</span><span class="kwrd">&gt;</span>
            @Html.DisplayFor(model =<span class="kwrd">&gt;</span> model.Phone)
        <span class="kwrd">&lt;/</span><span class="html">dd</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dt</span><span class="kwrd">&gt;</span>
            @Html.DisplayNameFor(model =<span class="kwrd">&gt;</span> model.Email)
        <span class="kwrd">&lt;/</span><span class="html">dt</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">dd</span><span class="kwrd">&gt;</span>
            @Html.DisplayFor(model =<span class="kwrd">&gt;</span> model.Email)
        <span class="kwrd">&lt;/</span><span class="html">dd</span><span class="kwrd">&gt;</span>
    <span class="kwrd">&lt;/</span><span class="html">dl</span><span class="kwrd">&gt;</span>
<span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
<span class="kwrd">&lt;</span><span class="html">p</span><span class="kwrd">&gt;</span>
    @Html.ActionLink("Edit", "Edit", new { id = Model.Id }) |
    @Html.ActionLink("Back to List", "Index")
<span class="kwrd">&lt;/</span><span class="html">p</span><span class="kwrd">&gt;</span>
</div>



<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="index-list-view.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="edit-view.html" class="btn btn-default pull-right">Next <i class="glyphicon glyphicon-chevron-right"></i></a>
</div>
</div>
