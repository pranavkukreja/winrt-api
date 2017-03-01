---
-api-id: T:Windows.UI.Xaml.Controls.ControlTemplate
-api-type: winrt class
---

<!-- Class syntax.
public class ControlTemplate : Windows.UI.Xaml.FrameworkTemplate, Windows.UI.Xaml.Controls.IControlTemplate
-->

# Windows.UI.Xaml.Controls.ControlTemplate

## -description
Defines the element tree that is used as the control template for a control.

## -xaml-syntax
```xaml
<ControlTemplate ...>
    templateRootElement
</ControlTemplate>
```


## -remarks
[ControlTemplate](controltemplate.md) is used as the value of the [Control.Template](control_template.md) property, which defines the visuals of a control by applying the template. You almost always define a [ControlTemplate](controltemplate.md) as a XAML resource, using an implicit key [TargetType](../windows.ui.xaml/style_targettype.md) that is the same as a [Style](../windows.ui.xaml/style.md) that sets [Control.Template](control_template.md) with a [Setter](../windows.ui.xaml/setter.md). You rarely if ever assign a value for [Control.Template](control_template.md) directly on a control instance.

There are really only two properties you use when defining a [ControlTemplate](controltemplate.md): the [TargetType](controltemplate_targettype.md), and the implicit XAML content. [ControlTemplate](controltemplate.md) inherits the implicit XAML content behavior from its [FrameworkTemplate](../windows.ui.xaml/frameworktemplate.md) parent. Basically the element contained within a [ControlTemplate](controltemplate.md) as defined in XAML is assigning a root element for a further structure of XAML elements that define the template. This is setting a "Template" property that can't subsequently be examined by code and only has meaning for how the XAML parser assigns content for controls based on applying that template.

To have its content be set from a [ControlTemplate](controltemplate.md), a control element must be a true [Control](control.md) subclass, so that it has the [Control.Template](control_template.md) property. There are other cases where templates apply content but this usually involves one of the other [FrameworkTemplate](../windows.ui.xaml/frameworktemplate.md) derived template classes ([DataTemplate](../windows.ui.xaml/datatemplate.md) or [ItemsPanelTemplate](itemspaneltemplate.md)).

Control templates provide the visuals and parts that make up an instance of a control as it appears in an app's UI. At run time, the template has already been applied, and so all the parts that were created out of the template are now truly parts of the control, and can be accessed by techniques such as examining the XAML namescopes from within control content or using the [VisualTreeHelper](../windows.ui.xaml.media/visualtreehelper.md) class. Events such as the input events sometimes expose the parts of a control that came from the applied control template.

There are ways to access template-defined content either before or after the template is applied to a specific control instance; see [OnApplyTemplate](../windows.ui.xaml/frameworkelement_onapplytemplate.md) or [GetTemplateChild](control_gettemplatechild.md).

The actual point in time that a [ControlTemplate](controltemplate.md) is applied to a control instance can be detected because this invokes the [OnApplyTemplate](../windows.ui.xaml/frameworkelement_onapplytemplate.md) protected virtual method. So long as the control isn't sealed, you can subclass a control so that you have the opportunity to override [OnApplyTemplate](../windows.ui.xaml/frameworkelement_onapplytemplate.md). This override can be written to perform actions that wouldn't be possible prior to the template being applied. For example, you can wire event handlers to control parts, or set control properties to reference object parts that were created out of the template but didn't start with a [{TemplateBinding} markup extension](http://msdn.microsoft.com/library/fde71086-9d42-4287-89ed-8fbfcdf169dc) value.

### Learning more about the control template for a control

Each XAML control has a topic in the documentation that discusses the control template, including the resources consumed by that template and other style elements. For example, you can learn about the default XAML template for the [FlipView](flipview.md) control in the topic [FlipView styles and templates](http://msdn.microsoft.com/library/9db798b1-06b7-40e3-add2-c89676b2bfdb).

## -examples
The following example creates a simple [ControlTemplate](controltemplate.md) for a [Button](button.md). The control template contains one [Grid](grid.md) and specifies this behavior:


+ When the user puts the mouse over the [Button](button.md), the [Grid](grid.md) changes from green to red over one half second.
+ When the user moves the mouse away from the button, the [Grid](grid.md) immediately changes back to green.




[!code-xml[11](../windows.ui.xaml.data/code/StylingTemplatingOverview/csharp/ButtonStages.xaml#Snippet11)]

## -see-also
[FrameworkTemplate](../windows.ui.xaml/frameworktemplate.md), [DataTemplate](../windows.ui.xaml/datatemplate.md), [OnApplyTemplate](../windows.ui.xaml/frameworkelement_onapplytemplate.md), [Control.Template](control_template.md), [Control](control.md), [Style](../windows.ui.xaml/style.md), [Quickstart: Control templates](http://msdn.microsoft.com/library/67c424ae-afb1-4560-a6a8-4a3506775d77)