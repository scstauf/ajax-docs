---
title: Localizing Strings
page_title: Localizing Strings | RadCalendar for ASP.NET AJAX Documentation
description: Localizing Strings
slug: calendar/accessibility-and-internationalization/localizing-strings
tags: localizing,strings
published: True
position: 4
---

# Localizing Strings


The **CultureInfo** property of the **RadCalendar** control and the **Culture** property of the **RadDatePicker**, **RadTimePicker** and **RadDateTimePicker** controls determine the strings that are used as month and day names. However, the **CultureInfo** property does not translate the other strings that appear in these controls.

On **RadCalendar** you may need to localize the strings that appear in the [month/year navigation]({%slug calendar/radcalendar/navigation-controls-settings%}). You can translate these strings using the **FastNavigationSettings** property:

````ASPNET
<telerik:RadCalendar
    ID="RadCalendar1"
    runat="server"
    CultureInfo="French (France)">
    <FastNavigationSettings
        CancelButtonCaption="Annuler"
        DateIsOutOfRangeMessage="La date est hors de gamme."
        OkButtonCaption="Accepter">
    </FastNavigationSettings>
</telerik:RadCalendar>
````


>note 
You can use the **FastNavigationSettings** property on the embedded popup calendar in a **RadDatePicker** or **RadDateTimePicker** control, as well as on a stand-alone **RadCalendar** control.
>


In addition, the tooltip strings that the various controls display may need to be localized. Most of the built-in tooltip strings are culture-neutral. For example, the built-in tooltip strings for the navigation controls on the **RadCalendar** title bar are simply pointers (e.g. ">") rather than text. However, the buttons on the **RadDatePicker**, **RadTimePicker** and **RadDateTimePicker** controls have tooltips that you may want to localize. To localize these strings, use the **ToolTip** property of the button, which can be accessed through the **DatePopupButton** and **TimePopupButton** properties.

To localize the string that appears in the header region of the embedded **TimeView** control, set its **HeaderText** property.

# See Also

 * [Tooltips]({%slug calendar/radcalendar/tooltips%})
