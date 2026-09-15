# Salesforce-Coding-Standards 👨‍💻✏️📐
Very similar to the GNU Coding Standards written by Richard Stallman and other GNU Project volunteers 🐃

## Can be used by AI or humans for coding …
 * ✅ Salesforce Apex Classes and Triggers
 * ✅ C/C++
 * ✅ Java

## ✅ Indent code using Allman style
https://en.wikipedia.org/wiki/Indentation_style#Allman_style

 * Code is indented using Allman Style — opening curly brace brackets are on new
 * lines to vertically align with closing curly brace brackets — and not in K&R
 * style which is taught in most schools, textbooks, and websites — where the
 * opening brace is on the previous line, and never aligns with the closing brace.
 * 
 * All code is contained within an 80 character right margin, preventing an ugly
 * horizontal scroll bar.
 * Indentations are tabs, not spaces, to reduce the number of characters used as
 * Apex has a limit of 6 MB per org.
 *
 * Single SOQL statments are broken into multiple lines, in a staircase indentation.

❌ ❎ don't use


comments should always contain at least 1 emoji

use spaces


# Rule 2: Reduce Nesting/Indentation and Exit Early: 🪺

## Do this. Reaches 2 levels of nesting/indentation: ✅🪺

### Reaches 2 levels of nesting: 🪺

```Apex
if (Org_Specific_Custom_Setting__c.getInstance()?.Run_All_Triggers__c == false)
{
    return;
}

TriggerHandler handler = new AccountTriggerHandler(Trigger.isExecuting, Trigger.size);
switch on Trigger.operationType
{
    when BEFORE_INSERT
    {
        handler.beforeInsert(Trigger.new);
    }
    when BEFORE_UPDATE
    {
        handler.beforeUpdate(Trigger.old, Trigger.new, Trigger.oldMap, Trigger.newMap);
    }
    when BEFORE_DELETE
    {
        handler.beforeDelete(Trigger.old, Trigger.oldMap);
    }
    when AFTER_INSERT
    {
        handler.afterInsert(Trigger.new, Trigger.newMap);
    }
    when AFTER_UPDATE
    {
        handler.afterUpdate(Trigger.old, Trigger.new, Trigger.oldMap, Trigger.newMap);
    }
    when AFTER_DELETE
    {
        handler.afterDelete(Trigger.old, Trigger.oldMap);
    }
    when AFTER_UNDELETE
    {
        handler.afterUndelete(Trigger.new, Trigger.newMap);
    }
}
```

## Not this. Reaches 3 levels of nesting/indentation. And literally indents almost the entire content of the Trigger inside an IF: ⛔🚫

### Reaches 3 levels of nesting: 🪺

```Apex
if (Org_Specific_Custom_Setting__c.getInstance()?.Run_All_Triggers__c ?? true)
{
    TriggerHandler handler = new AccountTriggerHandler(Trigger.isExecuting, Trigger.size);
    switch on Trigger.operationType
    {
        when BEFORE_INSERT
        {
            handler.beforeInsert(Trigger.new);
        }
        when BEFORE_UPDATE
        {
            handler.beforeUpdate(Trigger.old, Trigger.new, Trigger.oldMap, Trigger.newMap);
        }
        when BEFORE_DELETE
        {
            handler.beforeDelete(Trigger.old, Trigger.oldMap);
        }
        when AFTER_INSERT
        {
            Handler.afterInsert(Trigger.new, Trigger.newMap);
        }
        when AFTER_UPDATE
        {
            handler.afterUpdate(Trigger.old, Trigger.new, Trigger.oldMap, Trigger.newMap);
        }
        when AFTER_DELETE
        {
            handler.afterDelete(Trigger.old, Trigger.oldMap);
        }
        when AFTER_UNDELETE
        {
            handler.afterUndelete(Trigger.new, Trigger.newMap);
        }
    }
}


