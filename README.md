
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

For its forms, the [SPFx Property Pane](https://reactjs.org/docs/introducing-jsx.html) (PP) relies on a declarative model:

```typescript
groupFields: [
  PropertyPaneTextField('description', {label: strings.DescriptionFieldLabel}),
  PropertyPaneHorizontalRule(),
  PropertyPaneToggle('toggleProperty', toggleControlProperties),
  ...
```

The package includes:
-	A generic control **PropertyPaneWrap** for use in the Property Pane configuration

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
                }),                ...
```

## Samples (work in progress)

-	PnP SPFx controls: showcase the use of the controls library for both Web Part body and Property Pane.
-	Fluent UI Northstar: showcase reuse of controls directly from the library samples.
-	HTML 5: showcase the use of HTML elements in the Property Pane.
-	MGT: showcase MGT components in the Property Pane.

## Solution

Solution|Author(s)
--------|---------
property-pane-wrap | [Christophe Humbert](https://github.com/PathToSharePoint)

## Version history

Version|Date|Comments
-------|----|--------
0.1.0|Jan 25, 2022|First release

## Help

For issues, comments or questions, please reach out to Christophe on twitter ([Path2SharePoint](https://twitter.com/Path2SharePoint/)), github ([PathToSharePoint](https://github.com/PathToSharePoint)), or stackoverflow ([Christophe](https://stackoverflow.com/users/485406/christophe)) with the hashtag #PropertyPanePortal.

## Disclaimer

**THIS CODE IS PROVIDED *AS IS* WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**
