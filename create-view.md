---
layout: module
title: Module 9&#58; Add the Create View
---

In this module, you will add a Create View to demonstrate how to create a new Contact.

Using MVC Scaffolding, we can build out the view based on the Model classes scaffolded based on the Salesforce objects.


- Within the Controller.Create Method, right-click and select **Add View**
  - View name: **Create**
  - Template: **Create**
  - Model: **Contact ([YourProjectName].Models.Salesforce)**
- Click Add
- Replace the contents of the razor file with the following code:
> **Note:** Replace the @model namespace WebApplication1 with the namespace of your project


<button id="click2copy" data-clipboard-target="clipdata" data-text-type="code">Copy to Clipboard</button>


```html
@model WebApplication1.Models.Salesforce.Contact
@{
    ViewBag.Title = "Create";
}
<h2>Create</h2>
@using (Html.BeginForm()) {
    @Html.AntiForgeryToken()
    <div class="form-horizontal">
        <h4>Contact</h4>
        <hr />
        @Html.ValidationSummary(true, "", new { @class = "text-danger" })
        <div class="form-group">
            @Html.LabelFor(model => model.Salutation, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.Salutation, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.Salutation, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            @Html.LabelFor(model => model.FirstName, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.FirstName, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.FirstName, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            @Html.LabelFor(model => model.LastName, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.LastName, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.LastName, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            @Html.LabelFor(model => model.MailingStreet, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.MailingStreet, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.MailingStreet, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            @Html.LabelFor(model => model.MailingCity, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.MailingCity, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.MailingCity, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            @Html.LabelFor(model => model.MailingState, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.MailingState, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.MailingState, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            @Html.LabelFor(model => model.MailingPostalCode, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.MailingPostalCode, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.MailingPostalCode, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            @Html.LabelFor(model => model.MailingCountry, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.MailingCountry, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.MailingCountry, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            @Html.LabelFor(model => model.Phone, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.Phone, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.Phone, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            @Html.LabelFor(model => model.Email, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.Email, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.Email, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            <div class="col-md-offset-2 col-md-10">
                <input type="submit" value="Create" class="btn btn-default" />
            </div>
        </div>
    </div>
}
<div>
    @Html.ActionLink("Back to List", "Index")
</div>
@section Scripts {
    @Scripts.Render("~/bundles/jqueryval")
}
```


<div style="display: none;" id="clipdata">
@model WebApplication1.Models.Salesforce.Contact
@{
    ViewBag.Title = "Create";
}
<span class="kwrd">&lt;</span><span class="html">h2</span><span class="kwrd">&gt;</span>Create<span class="kwrd">&lt;/</span><span class="html">h2</span><span class="kwrd">&gt;</span>
@using (Html.BeginForm()) {
    @Html.AntiForgeryToken()
    <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="form-horizontal"</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">h4</span><span class="kwrd">&gt;</span>Contact<span class="kwrd">&lt;/</span><span class="html">h4</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">hr</span> <span class="kwrd">/&gt;</span>
        @Html.ValidationSummary(true, "", new { @class = "text-danger" })
        <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="form-group"</span><span class="kwrd">&gt;</span>
            @Html.LabelFor(model =<span class="kwrd">&gt;</span> model.Salutation, htmlAttributes: new { @class = "control-label col-md-2" })
            <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="col-md-10"</span><span class="kwrd">&gt;</span>
                @Html.EditorFor(model =<span class="kwrd">&gt;</span> model.Salutation, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model =<span class="kwrd">&gt;</span> model.Salutation, "", new { @class = "text-danger" })
            <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="form-group"</span><span class="kwrd">&gt;</span>
            @Html.LabelFor(model =<span class="kwrd">&gt;</span> model.FirstName, htmlAttributes: new { @class = "control-label col-md-2" })
            <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="col-md-10"</span><span class="kwrd">&gt;</span>
                @Html.EditorFor(model =<span class="kwrd">&gt;</span> model.FirstName, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model =<span class="kwrd">&gt;</span> model.FirstName, "", new { @class = "text-danger" })
            <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="form-group"</span><span class="kwrd">&gt;</span>
            @Html.LabelFor(model =<span class="kwrd">&gt;</span> model.LastName, htmlAttributes: new { @class = "control-label col-md-2" })
            <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="col-md-10"</span><span class="kwrd">&gt;</span>
                @Html.EditorFor(model =<span class="kwrd">&gt;</span> model.LastName, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model =<span class="kwrd">&gt;</span> model.LastName, "", new { @class = "text-danger" })
            <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="form-group"</span><span class="kwrd">&gt;</span>
            @Html.LabelFor(model =<span class="kwrd">&gt;</span> model.MailingStreet, htmlAttributes: new { @class = "control-label col-md-2" })
            <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="col-md-10"</span><span class="kwrd">&gt;</span>
                @Html.EditorFor(model =<span class="kwrd">&gt;</span> model.MailingStreet, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model =<span class="kwrd">&gt;</span> model.MailingStreet, "", new { @class = "text-danger" })
            <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="form-group"</span><span class="kwrd">&gt;</span>
            @Html.LabelFor(model =<span class="kwrd">&gt;</span> model.MailingCity, htmlAttributes: new { @class = "control-label col-md-2" })
            <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="col-md-10"</span><span class="kwrd">&gt;</span>
                @Html.EditorFor(model =<span class="kwrd">&gt;</span> model.MailingCity, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model =<span class="kwrd">&gt;</span> model.MailingCity, "", new { @class = "text-danger" })
            <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="form-group"</span><span class="kwrd">&gt;</span>
            @Html.LabelFor(model =<span class="kwrd">&gt;</span> model.MailingState, htmlAttributes: new { @class = "control-label col-md-2" })
            <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="col-md-10"</span><span class="kwrd">&gt;</span>
                @Html.EditorFor(model =<span class="kwrd">&gt;</span> model.MailingState, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model =<span class="kwrd">&gt;</span> model.MailingState, "", new { @class = "text-danger" })
            <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="form-group"</span><span class="kwrd">&gt;</span>
            @Html.LabelFor(model =<span class="kwrd">&gt;</span> model.MailingPostalCode, htmlAttributes: new { @class = "control-label col-md-2" })
            <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="col-md-10"</span><span class="kwrd">&gt;</span>
                @Html.EditorFor(model =<span class="kwrd">&gt;</span> model.MailingPostalCode, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model =<span class="kwrd">&gt;</span> model.MailingPostalCode, "", new { @class = "text-danger" })
            <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="form-group"</span><span class="kwrd">&gt;</span>
            @Html.LabelFor(model =<span class="kwrd">&gt;</span> model.MailingCountry, htmlAttributes: new { @class = "control-label col-md-2" })
            <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="col-md-10"</span><span class="kwrd">&gt;</span>
                @Html.EditorFor(model =<span class="kwrd">&gt;</span> model.MailingCountry, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model =<span class="kwrd">&gt;</span> model.MailingCountry, "", new { @class = "text-danger" })
            <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="form-group"</span><span class="kwrd">&gt;</span>
            @Html.LabelFor(model =<span class="kwrd">&gt;</span> model.Phone, htmlAttributes: new { @class = "control-label col-md-2" })
            <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="col-md-10"</span><span class="kwrd">&gt;</span>
                @Html.EditorFor(model =<span class="kwrd">&gt;</span> model.Phone, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model =<span class="kwrd">&gt;</span> model.Phone, "", new { @class = "text-danger" })
            <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="form-group"</span><span class="kwrd">&gt;</span>
            @Html.LabelFor(model =<span class="kwrd">&gt;</span> model.Email, htmlAttributes: new { @class = "control-label col-md-2" })
            <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="col-md-10"</span><span class="kwrd">&gt;</span>
                @Html.EditorFor(model =<span class="kwrd">&gt;</span> model.Email, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model =<span class="kwrd">&gt;</span> model.Email, "", new { @class = "text-danger" })
            <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="form-group"</span><span class="kwrd">&gt;</span>
            <span class="kwrd">&lt;</span><span class="html">div</span> <span class="attr">class</span><span class="kwrd">="col-md-offset-2 col-md-10"</span><span class="kwrd">&gt;</span>
                <span class="kwrd">&lt;</span><span class="html">input</span> <span class="attr">type</span><span class="kwrd">="submit"</span> <span class="attr">value</span><span class="kwrd">="Create"</span> <span class="attr">class</span><span class="kwrd">="btn btn-default"</span> <span class="kwrd">/&gt;</span>
            <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
        <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
    <span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
}
<span class="kwrd">&lt;</span><span class="html">div</span><span class="kwrd">&gt;</span>
    @Html.ActionLink("Back to List", "Index")
<span class="kwrd">&lt;/</span><span class="html">div</span><span class="kwrd">&gt;</span>
@section Scripts {
    @Scripts.Render("~/bundles/jqueryval")
}
</div>



<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="delete-view.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="runit-view.html" class="btn btn-default pull-right">Next <i class="glyphicon glyphicon-chevron-right"></i></a>
</div>
</div>
