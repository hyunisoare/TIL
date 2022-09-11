```C#
<%@ Page Title="Home Page" Language="C#"
 ***MaintainScrollPositionOnPostback="true"***
    MasterPageFile="~/Site.master" AutoEventWireup="true"
    CodeBehind="Default.aspx.cs" Inherits="PageDirectives._Default" %>
```

By setting the MaintainScrollPositionOnPostback to "true" the web forms infrastructure, specifically the page class 
automatically output some little bit of JavaScript. And it ables to select the elements. 