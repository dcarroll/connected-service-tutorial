---
layout: module
title: Module 3&#58; Create MVC Controller
---

In this module, you set up an MVC Controller to orchestrate the various views that will be created in the following modules.

- Right click on the Controllers folder and select Add-->Controller...
- Select MVC 5 Controller - Empty
- Name it: ContactsController
- Replace the contents of the Controller with the following code:
- Replace the namespace WebApplication1 with the namespace of your project

# Implement the controller as follows:

<button id="click2copy" data-clipboard-target="clipdata" data-text-type="code">Copy to Clipboard</button>
<pre>
```csharp
using Salesforce.Common.Models;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Net;
using System.Threading.Tasks;
using System.Web;
using System.Web.Mvc;
using WebApplication1.Models.Salesforce;
using WebApplication1.Salesforce;
namespace WebApplication1.Controllers
{
    public class ContactsController : Controller
    {
        /* Note: the SOQL Field list, and Binding Property list have subtle differences as custom properties may be mapped with the JsonProperty attribute to remove __c */
        const string _ContactsPostBinding = "Id,Salutation,FirstName,LastName,MailingStreet,MailingCity,MailingState,MailingPostalCode,MailingCountry,Phone,Email";
        /* GET: Contacts */
        public async Task<ActionResult> Index()
        {
            IEnumerable<Contact> selectedContacts = Enumerable.Empty<Contact>();
            try
            {
                selectedContacts = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                    async (client) =>
                    {
                        QueryResult<Contact> contacts =
                            await client.QueryAsync<Contact>("SELECT Id, Salutation, FirstName, LastName, MailingCity, MailingState, MailingCountry From Contact");
                        return contacts.records;
                    }
                    );
            }
            catch (Exception e)
            {
                this.ViewBag.OperationName = "query Salesforce Contacts";
                this.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(this.Request.Url.ToString());
                this.ViewBag.ErrorMessage = e.Message;
            }
            if (this.ViewBag.ErrorMessage == "AuthorizationRequired")
            {
                return Redirect(this.ViewBag.AuthorizationUrl);
            }
            return View(selectedContacts);
        }

        public async Task<ActionResult> Details(string id)
        {
            IEnumerable<Contact> selectedContacts = Enumerable.Empty<Contact>();
            try
            {
                selectedContacts = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                    async (client) =>
                    {
                        QueryResult<Contact> contacts =
                            await client.QueryAsync<Contact>("SELECT Id, Salutation, FirstName, LastName, MailingStreet, MailingCity, MailingState, MailingPostalCode, MailingCountry, Phone, Email From Contact Where Id = '" + id + "'");
                        return contacts.records;
                    }
                    );
            }
            catch (Exception e)
            {
                this.ViewBag.OperationName = "Salesforce Contacts Details";
                this.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(this.Request.Url.ToString());
                this.ViewBag.ErrorMessage = e.Message;
            }
            if (this.ViewBag.ErrorMessage == "AuthorizationRequired")
            {
                return Redirect(this.ViewBag.AuthorizationUrl);
            }
            return View(selectedContacts.FirstOrDefault());
        }

        public async Task<ActionResult> Edit(string id)
        {
            IEnumerable<Contact> selectedContacts = Enumerable.Empty<Contact>();
            try
            {
                selectedContacts = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                    async (client) =>
                    {
                        QueryResult<Contact> contacts =
                            await client.QueryAsync<Contact>("SELECT Id, Salutation, FirstName, LastName, MailingStreet, MailingCity, MailingState, MailingPostalCode, MailingCountry, Phone, Email From Contact Where Id= '" + id + "'");
                        return contacts.records;
                    }
                    );
            }
            catch (Exception e)
            {
                this.ViewBag.OperationName = "Edit Salesforce Contacts";
                this.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(this.Request.Url.ToString());
                this.ViewBag.ErrorMessage = e.Message;
            }
            if (this.ViewBag.ErrorMessage == "AuthorizationRequired")
            {
                return Redirect(this.ViewBag.AuthorizationUrl);
            }
            return View(selectedContacts.FirstOrDefault());
        }

        [HttpPost]
        [ValidateAntiForgeryToken]
        public async Task<ActionResult> Edit([Bind(Include = _ContactsPostBinding)] Contact contact)
        {
            SuccessResponse success = new SuccessResponse();
            try
            {
                success = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                    async (client) =>
                    {
                        success = await client.UpdateAsync("Contact", contact.Id, contact);
                        return success;
                    }
                    );
            }
            catch (Exception e)
            {
                this.ViewBag.OperationName = "Edit Salesforce Contact";
                this.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(this.Request.Url.ToString());
                this.ViewBag.ErrorMessage = e.Message;
            }
            if (this.ViewBag.ErrorMessage == "AuthorizationRequired")
            {
                return Redirect(this.ViewBag.AuthorizationUrl);
            }
            if (success.success == "true")
            {
                return RedirectToAction("Index");
            }
            else
            {
                return View(contact);
            }
        }

        public async Task<ActionResult> Delete(string id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            IEnumerable<Contact> selectedContacts = Enumerable.Empty<Contact>();
            try
            {
                selectedContacts = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                async (client) =>
                {
                    /* Query the properties you'll display for the user to confirm they wish to delete this Contact*/
                    QueryResult<Contact> contacts =
                        await client.QueryAsync<Contact>(string.Format("SELECT Id, FirstName, LastName, MailingCity, MailingState, MailingCountry From Contact Where Id='{0}'", id));
                    return contacts.records;
                }
                );
            }
            catch (Exception e)
            {
                this.ViewBag.OperationName = "query Salesforce Contacts";
                this.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(this.Request.Url.ToString());
                this.ViewBag.ErrorMessage = e.Message;
            }
            if (this.ViewBag.ErrorMessage == "AuthorizationRequired")
            {
                return Redirect(this.ViewBag.AuthorizationUrl);
            }
            if (selectedContacts.Count() == 0)
            {
                return View();
            }
            else
            {
                return View(selectedContacts.FirstOrDefault());
            }
        }

        [HttpPost, ActionName("Delete")]
        [ValidateAntiForgeryToken]
        public async Task<ActionResult> DeleteConfirmed(string id)
        {
            bool success = false;
            try
            {
                success = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                    async (client) =>
                    {
                        success = await client.DeleteAsync("Contact", id);
                        return success;
                    }
                    );
            }
            catch (Exception e)
            {
                this.ViewBag.OperationName = "Delete Salesforce Contacts";
                this.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(this.Request.Url.ToString());
                this.ViewBag.ErrorMessage = e.Message;
            }
            if (this.ViewBag.ErrorMessage == "AuthorizationRequired")
            {
                return Redirect(this.ViewBag.AuthorizationUrl);
            }
            if (success)
            {
                return RedirectToAction("Index");
            }
            else
            {
                return View();
            }
        }

        public ActionResult Create()
        {
            return View();
        }

        [HttpPost]
        [ValidateAntiForgeryToken]
        public async Task<ActionResult> Create([Bind(Include = _ContactsPostBinding)] Contact contact)
        {
            String id = String.Empty;
            try
            {
                id = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                    async (client) =>
                    {
                        return await client.CreateAsync("Contact", contact);
                    }
                    );
            }
            catch (Exception e)
            {
                this.ViewBag.OperationName = "Create Salesforce Contact";
                this.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(this.Request.Url.ToString());
                this.ViewBag.ErrorMessage = e.Message;
            }
            if (this.ViewBag.ErrorMessage == "AuthorizationRequired")
            {
                return Redirect(this.ViewBag.AuthorizationUrl);
            }
            if (this.ViewBag.ErrorMessage == null)
            {
                return RedirectToAction("Index");
            } else
            {
                return View(contact);
            }
        }
    }
} 
```
</pre>






<pre style="display: none;" id="html">
<span class="kwrd">using</span> Salesforce.Common.Models;
<span class="kwrd">using</span> System;
<span class="kwrd">using</span> System.Collections.Generic;
<span class="kwrd">using</span> System.Linq;
<span class="kwrd">using</span> System.Net;
<span class="kwrd">using</span> System.Threading.Tasks;
<span class="kwrd">using</span> System.Web;
<span class="kwrd">using</span> System.Web.Mvc;
<span class="kwrd">using</span> WebApplication1.Models.Salesforce;
<span class="kwrd">using</span> WebApplication1.Salesforce;
<span class="kwrd">namespace</span> WebApplication1.Controllers
{
    <span class="kwrd">public</span> <span class="kwrd">class</span> ContactsController : Controller
    {
        <span class="rem">// Note: the SOQL Field list, and Binding Property list have subtle differences as custom properties may be mapped with the JsonProperty attribute to remove __c</span>
        <span class="kwrd">const</span> <span class="kwrd">string</span> _ContactsPostBinding = <span class="str">"Id,Salutation,FirstName,LastName,MailingStreet,MailingCity,MailingState,MailingPostalCode,MailingCountry,Phone,Email"</span>;
        <span class="rem">// GET: Contacts</span>
        <span class="kwrd">public</span> async Task&lt;ActionResult&gt; Index()
        {
            IEnumerable&lt;Contact&gt; selectedContacts = Enumerable.Empty&lt;Contact&gt;();
            <span class="kwrd">try</span>
            {
                selectedContacts = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                    async (client) =&gt;
                    {
                        QueryResult&lt;Contact&gt; contacts =
                            await client.QueryAsync&lt;Contact&gt;(<span class="str">"SELECT Id, Salutation, FirstName, LastName, MailingCity, MailingState, MailingCountry From Contact"</span>);
                        <span class="kwrd">return</span> contacts.records;
                    }
                    );
            }
            <span class="kwrd">catch</span> (Exception e)
            {
                <span class="kwrd">this</span>.ViewBag.OperationName = <span class="str">"query Salesforce Contacts"</span>;
                <span class="kwrd">this</span>.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(<span class="kwrd">this</span>.Request.Url.ToString());
                <span class="kwrd">this</span>.ViewBag.ErrorMessage = e.Message;
            }
            <span class="kwrd">if</span> (<span class="kwrd">this</span>.ViewBag.ErrorMessage == <span class="str">"AuthorizationRequired"</span>)
            {
                <span class="kwrd">return</span> Redirect(<span class="kwrd">this</span>.ViewBag.AuthorizationUrl);
            }
            <span class="kwrd">return</span> View(selectedContacts);
        }

        <span class="kwrd">public</span> async Task&lt;ActionResult&gt; Details(<span class="kwrd">string</span> id)
        {
            IEnumerable&lt;Contact&gt; selectedContacts = Enumerable.Empty&lt;Contact&gt;();
            <span class="kwrd">try</span>
            {
                selectedContacts = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                    async (client) =&gt;
                    {
                        QueryResult&lt;Contact&gt; contacts =
                            await client.QueryAsync&lt;Contact&gt;(<span class="str">"SELECT Id, Salutation, FirstName, LastName, MailingStreet, MailingCity, MailingState, MailingPostalCode, MailingCountry, Phone, Email From Contact Where Id = '"</span> + id + <span class="str">"'"</span>);
                        <span class="kwrd">return</span> contacts.records;
                    }
                    );
            }
            <span class="kwrd">catch</span> (Exception e)
            {
                <span class="kwrd">this</span>.ViewBag.OperationName = <span class="str">"Salesforce Contacts Details"</span>;
                <span class="kwrd">this</span>.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(<span class="kwrd">this</span>.Request.Url.ToString());
                <span class="kwrd">this</span>.ViewBag.ErrorMessage = e.Message;
            }
            <span class="kwrd">if</span> (<span class="kwrd">this</span>.ViewBag.ErrorMessage == <span class="str">"AuthorizationRequired"</span>)
            {
                <span class="kwrd">return</span> Redirect(<span class="kwrd">this</span>.ViewBag.AuthorizationUrl);
            }
            <span class="kwrd">return</span> View(selectedContacts.FirstOrDefault());
        }

        <span class="kwrd">public</span> async Task&lt;ActionResult&gt; Edit(<span class="kwrd">string</span> id)
        {
            IEnumerable&lt;Contact&gt; selectedContacts = Enumerable.Empty&lt;Contact&gt;();
            <span class="kwrd">try</span>
            {
                selectedContacts = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                    async (client) =&gt;
                    {
                        QueryResult&lt;Contact&gt; contacts =
                            await client.QueryAsync&lt;Contact&gt;(<span class="str">"SELECT Id, Salutation, FirstName, LastName, MailingStreet, MailingCity, MailingState, MailingPostalCode, MailingCountry, Phone, Email From Contact Where Id= '"</span> + id + <span class="str">"'"</span>);
                        <span class="kwrd">return</span> contacts.records;
                    }
                    );
            }
            <span class="kwrd">catch</span> (Exception e)
            {
                <span class="kwrd">this</span>.ViewBag.OperationName = <span class="str">"Edit Salesforce Contacts"</span>;
                <span class="kwrd">this</span>.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(<span class="kwrd">this</span>.Request.Url.ToString());
                <span class="kwrd">this</span>.ViewBag.ErrorMessage = e.Message;
            }
            <span class="kwrd">if</span> (<span class="kwrd">this</span>.ViewBag.ErrorMessage == <span class="str">"AuthorizationRequired"</span>)
            {
                <span class="kwrd">return</span> Redirect(<span class="kwrd">this</span>.ViewBag.AuthorizationUrl);
            }
            <span class="kwrd">return</span> View(selectedContacts.FirstOrDefault());
        }

        [HttpPost]
        [ValidateAntiForgeryToken]
        <span class="kwrd">public</span> async Task&lt;ActionResult&gt; Edit([Bind(Include = _ContactsPostBinding)] Contact contact)
        {
            SuccessResponse success = <span class="kwrd">new</span> SuccessResponse();
            <span class="kwrd">try</span>
            {
                success = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                    async (client) =&gt;
                    {
                        success = await client.UpdateAsync(<span class="str">"Contact"</span>, contact.Id, contact);
                        <span class="kwrd">return</span> success;
                    }
                    );
            }
            <span class="kwrd">catch</span> (Exception e)
            {
                <span class="kwrd">this</span>.ViewBag.OperationName = <span class="str">"Edit Salesforce Contact"</span>;
                <span class="kwrd">this</span>.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(<span class="kwrd">this</span>.Request.Url.ToString());
                <span class="kwrd">this</span>.ViewBag.ErrorMessage = e.Message;
            }
            <span class="kwrd">if</span> (<span class="kwrd">this</span>.ViewBag.ErrorMessage == <span class="str">"AuthorizationRequired"</span>)
            {
                <span class="kwrd">return</span> Redirect(<span class="kwrd">this</span>.ViewBag.AuthorizationUrl);
            }
            <span class="kwrd">if</span> (success.success == <span class="str">"true"</span>)
            {
                <span class="kwrd">return</span> RedirectToAction(<span class="str">"Index"</span>);
            }
            <span class="kwrd">else</span>
            {
                <span class="kwrd">return</span> View(contact);
            }
        }

        <span class="kwrd">public</span> async Task&lt;ActionResult&gt; Delete(<span class="kwrd">string</span> id)
        {
            <span class="kwrd">if</span> (id == <span class="kwrd">null</span>)
            {
                <span class="kwrd">return</span> <span class="kwrd">new</span> HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            IEnumerable&lt;Contact&gt; selectedContacts = Enumerable.Empty&lt;Contact&gt;();
            <span class="kwrd">try</span>
            {
                selectedContacts = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                async (client) =&gt;
                {
                    <span class="rem">// Query the properties you'll display for the user to confirm they wish to delete this Contact</span>
                    QueryResult&lt;Contact&gt; contacts =
                        await client.QueryAsync&lt;Contact&gt;(<span class="kwrd">string</span>.Format(<span class="str">"SELECT Id, FirstName, LastName, MailingCity, MailingState, MailingCountry From Contact Where Id='{0}'"</span>, id));
                    <span class="kwrd">return</span> contacts.records;
                }
                );
            }
            <span class="kwrd">catch</span> (Exception e)
            {
                <span class="kwrd">this</span>.ViewBag.OperationName = <span class="str">"query Salesforce Contacts"</span>;
                <span class="kwrd">this</span>.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(<span class="kwrd">this</span>.Request.Url.ToString());
                <span class="kwrd">this</span>.ViewBag.ErrorMessage = e.Message;
            }
            <span class="kwrd">if</span> (<span class="kwrd">this</span>.ViewBag.ErrorMessage == <span class="str">"AuthorizationRequired"</span>)
            {
                <span class="kwrd">return</span> Redirect(<span class="kwrd">this</span>.ViewBag.AuthorizationUrl);
            }
            <span class="kwrd">if</span> (selectedContacts.Count() == 0)
            {
                <span class="kwrd">return</span> View();
            }
            <span class="kwrd">else</span>
            {
                <span class="kwrd">return</span> View(selectedContacts.FirstOrDefault());
            }
        }

        [HttpPost, ActionName(<span class="str">"Delete"</span>)]
        [ValidateAntiForgeryToken]
        <span class="kwrd">public</span> async Task&lt;ActionResult&gt; DeleteConfirmed(<span class="kwrd">string</span> id)
        {
            <span class="kwrd">bool</span> success = <span class="kwrd">false</span>;
            <span class="kwrd">try</span>
            {
                success = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                    async (client) =&gt;
                    {
                        success = await client.DeleteAsync(<span class="str">"Contact"</span>, id);
                        <span class="kwrd">return</span> success;
                    }
                    );
            }
            <span class="kwrd">catch</span> (Exception e)
            {
                <span class="kwrd">this</span>.ViewBag.OperationName = <span class="str">"Delete Salesforce Contacts"</span>;
                <span class="kwrd">this</span>.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(<span class="kwrd">this</span>.Request.Url.ToString());
                <span class="kwrd">this</span>.ViewBag.ErrorMessage = e.Message;
            }
            <span class="kwrd">if</span> (<span class="kwrd">this</span>.ViewBag.ErrorMessage == <span class="str">"AuthorizationRequired"</span>)
            {
                <span class="kwrd">return</span> Redirect(<span class="kwrd">this</span>.ViewBag.AuthorizationUrl);
            }
            <span class="kwrd">if</span> (success)
            {
                <span class="kwrd">return</span> RedirectToAction(<span class="str">"Index"</span>);
            }
            <span class="kwrd">else</span>
            {
                <span class="kwrd">return</span> View();
            }
        }

        <span class="kwrd">public</span> ActionResult Create()
        {
            <span class="kwrd">return</span> View();
        }

        [HttpPost]
        [ValidateAntiForgeryToken]
        <span class="kwrd">public</span> async Task&lt;ActionResult&gt; Create([Bind(Include = _ContactsPostBinding)] Contact contact)
        {
            String id = String.Empty;
            <span class="kwrd">try</span>
            {
                id = await SalesforceService.MakeAuthenticatedClientRequestAsync(
                    async (client) =&gt;
                    {
                        <span class="kwrd">return</span> await client.CreateAsync(<span class="str">"Contact"</span>, contact);
                    }
                    );
            }
            <span class="kwrd">catch</span> (Exception e)
            {
                <span class="kwrd">this</span>.ViewBag.OperationName = <span class="str">"Create Salesforce Contact"</span>;
                <span class="kwrd">this</span>.ViewBag.AuthorizationUrl = SalesforceOAuthRedirectHandler.GetAuthorizationUrl(<span class="kwrd">this</span>.Request.Url.ToString());
                <span class="kwrd">this</span>.ViewBag.ErrorMessage = e.Message;
            }
            <span class="kwrd">if</span> (<span class="kwrd">this</span>.ViewBag.ErrorMessage == <span class="str">"AuthorizationRequired"</span>)
            {
                <span class="kwrd">return</span> Redirect(<span class="kwrd">this</span>.ViewBag.AuthorizationUrl);
            }
            <span class="kwrd">if</span> (<span class="kwrd">this</span>.ViewBag.ErrorMessage == <span class="kwrd">null</span>)
            {
                <span class="kwrd">return</span> RedirectToAction(<span class="str">"Index"</span>);
            } <span class="kwrd">else</span>
            {
                <span class="kwrd">return</span> View(contact);
            }
        }
    }
}
</pre>

<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="mvc-overview.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="edit-navigation-menu.html" class="btn btn-default pull-right">Next <i class="glyphicon glyphicon-chevron-right"></i></a>
</div>
</div>
