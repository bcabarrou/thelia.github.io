---
layout: form
title: customer profile update
form_name: thelia.front.customer.profile.update
sidebar: form
subnav: form_list_customer_updateprofile
fields:
    - { name: "title", mandatory: "true", description: "customer title ID. See [title loop](http://doc.thelia.net/en/documentation/loop/title.html)"}
    - { name: "firstname", mandatory: "true", description: "customer first name"}
    - { name: "lastname", mandatory: "true", description: "customer last name"}
    - { name: "email", mandatory: "true", description: "customer email address"}
    - { name: "newsletter", mandatory: "false", description: "If true, the customer is added to the newsletter subscribers list. If false, he/she is removed from this list."}
lang: en

---
```
{form name="thelia.front.customer.profile.update"}
<form id="form-register" class="form-horizontal" action="{url path="/account/update"}" method="post">
    {form_field form=$form field='success_url'}
        <input type="hidden" name="{$name}" value="{url path="/account"}" />
    {/form_field}

    {form_hidden_fields form=$form}

    {if $form_error}<div class="alert alert-danger">{$form_error_message}</div>{/if}

    <fieldset id="register-info" class="panel">
        <div class="panel-heading">
            {intl l="Personal Information"}
        </div>

        <div class="panel-body">
            {form_field form=$form field="title"}
                <div class="form-group group-title{if $error} has-error{/if}">
                    <label class="control-label" for="{$label_attr.for}">{$label}{if $required} <span class="required">*</span>{/if}</label>
                    <div class="control-input">
                        <select name="{$name}" id="{$label_attr.for}" class="form-control"{if $required} aria-required="true" required{/if}{if !$value || $error} autofocus{/if}>
                            <option value="">-- {intl l="Select Title"} --</option>
                            {loop type="title" name="country.list"}
                                <option value="{$ID}" {if $value == $ID}selected{/if} >{$LONG}</option>
                            {/loop}
                        </select>
                        {if $error}
                            <span class="help-block">{$message}</span>
                            {assign var="error_focus" value="true"}
                        {elseif !$value}
                            {assign var="error_focus" value="true"}
                        {/if}
                    </div>
                </div><!--/.form-group-->
            {/form_field}
            {form_field form=$form field="firstname"}
            <div class="form-group group-firstname {if $error}has-error{/if}">
                <label class="control-label" for="{$label_attr.for}">{$label}{if $required} <span class="required">*</span>{/if}</label>
                <div class="control-input">
                    <input type="text" name="{$name}" id="{$label_attr.for}" class="form-control" maxlength="255" placeholder="{intl l="Placeholder firstname"}" value="{$value}"{if $required} aria-required="true" required{/if}{if !isset($error_focus) && $error} autofocus{/if}>
                    {if $error }
                        <span class="help-block">{$message}</span>
                        {assign var="error_focus" value="true"}
                    {/if}
                </div>
            </div><!--/.form-group-->
            {/form_field}
            {form_field form=$form field="lastname"}
                <div class="form-group group-lastname {if $error}has-error{/if}">
                    <label class="control-label" for="{$label_attr.for}">{$label}{if $required} <span class="required">*</span>{/if}</label>
                    <div class="control-input">
                        <input type="text" name="{$name}" id="{$label_attr.for}" class="form-control" maxlength="255" placeholder="{intl l="Placeholder lastname"}" value="{$value}" {if $required} aria-required="true" required{/if}{if !isset($error_focus) && $error} autofocus{/if}>
                        {if $error }
                            <span class="help-block">{$message}</span>
                            {assign var="error_focus" value="true"}
                        {/if}
                    </div>
                </div><!--/.form-group-->
            {/form_field}
            {form_field form=$form field="email"}
            <div class="form-group group-email {if $error}has-error{/if}">
                <label class="control-label" for="{$label_attr.for}">{$label}{if $required} <span class="required">*</span>{/if}</label>

                <div class="control-input">
                    <input type="email" name="{$name}" id="{$label_attr.for}" class="form-control" maxlength="255" placeholder="{intl l="Placeholder email"}" value="{$smarty.get.email|default:$value}"{if $required} aria-required="true" required{/if}{if !isset($error_focus) && $error} autofocus{/if}>
                    {if $error }
                        <span class="help-block">{$message}</span>
                        {assign var="error_focus" value="true"}
                    {/if}
                </div>
            </div><!--/.form-group-->
            {/form_field}
        </div>
    </fieldset>

    {form_field form=$form field="newsletter"}
    <div class="form-group group-newsletter{if $error} has-error{/if}">
        <div class="control-input">
            <div class="checkbox">
                <label class="control-label" for="{$label_attr.for}">
                    <input type="checkbox" name="{$name}" id="{$label_attr.for}" value="{$value}"{if $checked} checked{/if}  {if $required} aria-required="true" required{/if}>{$label}
                </label>
                {if $error }
                    <span class="help-block">{$message}</span>
                {/if}
            </div>
        </div>
    </div><!--/.form-group-->
    {/form_field}

    <div class="form-group group-btn">
        <div class="control-btn">
            <button type="submit" class="btn btn-register">{intl l="Update"}</button>
        </div>
    </div><!--/.form-group-->
</form>
{/form}
```