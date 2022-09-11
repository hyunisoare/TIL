***Setting a Default Button***

- Setting the default button when a user hits the "enter" key can be done using the defaultButton attribute:
```C#
<form defaultButton="btnSearch" runat="server">
```

```C#
- The <asp:panel> control can override the defaultButton specified when the panel has focus:
<asp:Panel runat="server" defaultButton="btnOk">
...
<asp:Panel>
```

-Setting the default focus for a page can be done using the defaultFocus attribute:
```C#
<form defaultFocus="txtName" runat="server">
```
- Programmatic support for validating groups:
    - Page.SetFocus(control)
    - Page.SetFocus("ClientID")
    - txtName.Focus()
