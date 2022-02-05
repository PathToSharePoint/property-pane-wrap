
# Property Pane Wrap

## Applies to

[SharePoint Framework](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview)

## Compatibility

![SPFx 1.12](https://img.shields.io/badge/SPFx-1.12-green.svg) 
![React 16.x](https://img.shields.io/badge/React-16.x-green.svg) 
![Compatible with SharePoint Online](https://img.shields.io/badge/SharePoint%20Online-Compatible-green.svg)
![Does not work with SharePoint 2019](https://img.shields.io/badge/SharePoint%20Server%202019-Incompatible-red.svg "SharePoint Server 2019 requires SPFx 1.4.1 or lower")
![Does not work with SharePoint 2016 (Feature Pack 2)](https://img.shields.io/badge/SharePoint%20Server%202016%20(Feature%20Pack%202)-Incompatible-red.svg "SharePoint Server 2016 Feature Pack 2 requires SPFx 1.1")
![Hosted Workbench Compatible](https://img.shields.io/badge/Hosted%20Workbench-Compatible-green.svg)

## About the Property Pane Wrap

For its form controls, the [SPFx Property Pane](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/basics/integrate-with-property-pane) (PP) relies on a declarative model:

```typescript
groupFields: [
  PropertyPaneTextField('description', {label: strings.DescriptionFieldLabel}),
  PropertyPaneHorizontalRule(),
  PropertyPaneToggle('toggleProperty', toggleControlProperties),
  ...
```

But how would you add to the Property Pane a custom control, not covered by the built-in functions offered by Microsoft? For example a date picker or a dropdown with dynamic choices?

That's where the Property Pane Wrap comes into play. It lets you wrap a React component for insertion in the Property Pane.

## How to Use the Package

In your SPFx solution, import the package:

```
npm i property-pane-wrap
```

This will make the **PropertyPaneWrap** function available to your solution.

See the list of samples for detailed implementation. Below the high level steps.

1. Declare your custom property as you would usually do in HelloWorldWebPart.tsx.

2. Import PropertyPaneWrap to HelloWorldWebPart:
```typescript
import { PropertyPaneWrap } from 'property-pane-wrap';
```
3. Use PropertyPaneWrap in the Property Pane configuration:
```typescript
  protected getPropertyPaneConfiguration(): IPropertyPaneConfiguration {

    return {
      pages: [
        {
          header: {
            description: strings.PropertyPaneDescription
          },
          groups: [
            {
              groupName: strings.BasicGroupName,
              groupFields: [
                PropertyPaneTextField('description', {label: strings.DescriptionFieldLabel}),
                PropertyPaneHorizontalRule(),
                PropertyPaneWrap('mgtPeoplePicker', {
                  component: PeoplePicker,
                  props: {
                    selectionMode: "single",
                    selectionChanged: onSelectionChanged
                  }
                }),
                ...
```

## Samples (work in progress)

-	[React-PPW-MGT](https://github.com/PathToSharePoint/React-PPW-MGT): showcase Microsoft Graph Toolkit components in the SPFx Property Pane.
-	[React-PPW-FastFluentUI](https://github.com/PathToSharePoint/React-PPW-FastFluentUI): showcase Fluent UI Fast Web components in the SPFx Property Pane.
-	[React-PPW-PnPControls](https://github.com/PathToSharePoint/React-PPW-PnPControls): showcase the use of the PnP SPFx controls library in the SPFx Property Pane.


## Solution

Solution|Author(s)
--------|---------
property-pane-wrap | [Christophe Humbert](https://github.com/PathToSharePoint)

## Version history

Version|Date|Comments
-------|----|--------
0.1.0|Jan 25, 2022|First release
0.3.0|Feb 5, 2022|Code Cleanup

## Help

For issues, comments or questions, please reach out to Christophe on twitter ([Path2SharePoint](https://twitter.com/Path2SharePoint/)), github ([PathToSharePoint](https://github.com/PathToSharePoint)), or stackoverflow ([Christophe](https://stackoverflow.com/users/485406/christophe)) with the hashtag #PropertyPaneWrap.

## Disclaimer

**THIS CODE IS PROVIDED *AS IS* WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**
