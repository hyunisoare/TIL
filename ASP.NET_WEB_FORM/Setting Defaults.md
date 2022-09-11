***Setting a Default Button***

```C#
- Setting the default button when a user hits the "enter" key can be done using the defaultButton attribute:
<form defaultButton="btnSearch" runat="server">
```

- The <asp:panel> control can override the defaultButton specified when the panel has focus:
<asp:Panel runat="server" defaultButton="btnOk">
...
<asp:Panel>

-Setting the default focus for a page can be done using the defaultFocus attribute:
<form defaultFocus="txtName" runat="server">

- Programmatic support for validating groups:
    - Page.SetFocus(control)
    - Page.SetFocus("ClientID")
    - txtName.Focus()
