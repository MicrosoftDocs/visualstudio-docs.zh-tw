---
title: 啟用控制項的自動程式碼 UI 測試功能 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 24
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 331dabfe8e219383fdc04187482b17b9048886a9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302579"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>啟用控制項的自動程式化 UI 測試功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您實作自動程式化 UI 測試架構的支援，就可以更輕鬆地測試您的控制項。 您可以用累加方式加入不斷增加的支援層級。 您可以從支援錄製和播放以及屬性驗證開始。 您可以依此為建置基礎，讓自動程式碼 UI 測試產生器能夠辨識控制項的自訂屬性，並提供自訂類別，以從產生的程式碼存取那些屬性。 您也可以協助自動程式化 UI 測試產生器，以較接近所錄製動作之意圖的方式來擷取動作。

 **本主題內容：**

1. [藉由實作協助工具，支援錄製和播放以及屬性驗證](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)

2. [藉由實作屬性提供者，支援自訂屬性驗證](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)

3. [藉由實作類別來存取自訂屬性，支援程式碼產生](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)

4. [藉由實作動作篩選，支援意圖感知動作](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)

   ![CUIT&#95;Full](../test/media/cuit-full.png "CUIT_Full")

## <a name="recordandplayback"></a> 藉由實作協助工具，支援錄製和播放以及屬性驗證
 自動程式化 UI 測試產生器會擷取它在錄製期間遇到之控制項的相關資訊，然後產生程式碼，以重新執行該工作階段。 如果您的控制項不支援協助工具，自動程式碼 UI 測試產生器將會使用螢幕座標來擷取動作 (例如滑鼠點按)。 播放測試時，所產生的程式碼就會在相同的螢幕座標中發出這些滑鼠點按動作。 如果在播放測試時，您的控制項出現在螢幕上的不同位置，所產生的程式碼將無法在您的控制項上執行該動作。 如果是在不同的螢幕組態上、在不同環境中，或是在 UI 配置有所變更之後播放測試，這樣會導致失敗。

 ![CUIT&#95;RecordNoSupport](../test/media/cuit-recordnosupport.png "CUIT_RecordNoSupport")

 不過，如果您實作協助工具，當自動程式化 UI 測試產生器錄製測試並產生程式碼時，將會使用該協助工具來擷取控制項的相關資訊。 然後，當您執行測試時，即使控制項是在使用者介面中的其他地方，所產生的程式碼還是會對您的控制項重新執行這些事件。 測試作者也可以使用控制項的基本屬性來建立判斷提示。

 ![CUIT&#95;記錄](../test/media/cuit-record.png "CUIT_Record")

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>支援錄製和播放、屬性驗證，以及巡覽 Windows 表單控制項
 依照下列程序的概述，以及 <xref:System.Windows.Forms.AccessibleObject> 的詳細說明，為您的控制項實作協助工具。

 ![CUIT&#95;可存取](../test/media/cuit-accessible.png "CUIT_Accessible")

1. 實作衍生自 <xref:System.Windows.Forms.Control.ControlAccessibleObject> 的類別，並覆寫 <xref:System.Windows.Forms.Control.AccessibilityObject%2A> 屬性，以傳回您的類別物件。

    ```csharp
    public partial class ChartControl : UserControl
    {
        // Overridden to return the custom AccessibleObject for the control.
        protected override AccessibleObject CreateAccessibilityInstance()
        {
            return new ChartControlAccessibleObject(this);
        }

        // Inner class ChartControlAccessibleObject represents accessible information
        // associated with the ChartControl and is used when recording tests.
        public class ChartControlAccessibleObject : ControlAccessibleObject
        {
            ChartControl myControl;
            public ChartControlAccessibleObject(ChartControl ctrl)
                : base(ctrl)
            {
                myControl = ctrl;
            }
        }
    }
    ```

2. 覆寫可存取物件的 <xref:System.Windows.Forms.AccessibleObject.Role%2A>、<xref:System.Windows.Forms.AccessibleObject.State%2A>、<xref:System.Windows.Forms.AccessibleObject.GetChild%2A> 和 <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> 屬性和方法。

3. 為子控制項實作另一個協助工具物件，並覆寫子控制項的 <xref:System.Windows.Forms.Control.AccessibilityObject%2A> 屬性以傳回該協助工具物件。

4. 針對子控制項的協助工具物件，覆寫 <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>、<xref:System.Windows.Forms.AccessibleObject.Name%2A>、<xref:System.Windows.Forms.AccessibleObject.Parent%2A>、<xref:System.Windows.Forms.AccessibleObject.Role%2A>、<xref:System.Windows.Forms.AccessibleObject.State%2A>、<xref:System.Windows.Forms.AccessibleObject.Navigate%2A> 和 <xref:System.Windows.Forms.AccessibleObject.Select%2A> 屬性和方法。

> [!NOTE]
> 本主題一開始在此程序的 <xref:System.Windows.Forms.AccessibleObject> 中提供協助工具範例，然後在其餘程序中，以其做為建置基礎。 如果您想要建立協助工具範例的有效版本，請建立主控台應用程式，然後將 Program.cs 中的程式碼取代成該範例程式碼。 您必須將參考加入協助工具、System.Drawing 和 System.Windows.Forms。 您應將協助工具的 [內嵌 Interop 類型] 變更為 **False**，以消除建置警告。 您可以將專案的輸出類型從 [主控台應用程式] 變更為 [Windows 應用程式]，如此當您執行應用程式時，才不會出現主控台視窗。

## <a name="customproprties"></a> 藉由實作屬性提供者，支援自訂屬性驗證
 為記錄和播放以及屬性驗證實作基本支援之後，就可以藉由實作 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> 外掛程式，讓自動程式碼 UI 測試能夠使用控制項的自訂屬性。 例如，下列程序所建立的屬性提供者，能夠讓自動程式化 UI 測試存取圖表控制項的 CurveLegend 子控制項的狀態屬性。

 ![CUIT&#95;CustomProps](../test/media/cuit-customprops.png "CUIT_CustomProps")

### <a name="to-support-custom-property-validation"></a>支援自訂屬性驗證
 ![CUIT&#95;.props](../test/media/cuit-props.png "CUIT_Props")

1. 覆寫曲線圖例可存取物件的 <xref:System.Windows.Forms.AccessibleObject.Description%2A> 屬性，以描述字串來傳遞豐富的屬性值 (以分號 (;) 將其與主要描述分隔，如果您要實作多個屬性，也是以分號將彼此分隔)。

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add “;” and the state value to the end
                // of the curve legend’s description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

2. 藉由建立類別庫專案來建立控制項的 UI 測試擴充套件，並將參考加入協助工具、Microsoft.VisualStudio.TestTools.UITesting、Microsoft.VisualStudio.TestTools.UITest.Common 和 Microsoft.VisualStudio.TestTools.Extension。 將協助工具的 [內嵌 Interop 類型] 變更為 **False**。

3. 加入衍生自 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> 的屬性提供者類別。

    ```csharp
    using System;
    using System.Collections.Generic;
    using Accessibility;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        public class ChartControlPropertyProvider : UITestPropertyProvider
        {
        }
    }
    ```

4. 在 <xref:System.Collections.Generic.Dictionary%602> 中放置屬性名稱和屬性描述元，以實作屬性提供者。

    ```csharp
    // Define a map of property descriptors for CurveLegend
    private static Dictionary<string, UITestPropertyDescriptor> curveLegendPropertiesMap = null;
    private static Dictionary<string, UITestPropertyDescriptor> CurveLegendPropertiesMap
    {
        get
        {
            if (curveLegendPropertiesMap == null)
            {
                UITestPropertyAttributes read =
                    UITestPropertyAttributes.Readable |
                    UITestPropertyAttributes.DoNotGenerateProperties;
                curveLegendPropertiesMap =
                    new Dictionary<string, UITestPropertyDescriptor>
                        (StringComparer.OrdinalIgnoreCase);
                curveLegendPropertiesMap.Add("State",
                    new UITestPropertyDescriptor(typeof(string), read));
            }
            return curveLegendPropertiesMap;
        }
    }

    // return the property descriptor
    public override UITestPropertyDescriptor GetPropertyDescriptor(UITestControl uiTestControl, string propertyName)
    {
        return CurveLegendPropertiesMap[propertyName];
    }

    // return the property names
    public override ICollection<string> GetPropertyNames(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Chart") || uiTestControl.ControlType.NameEquals("Text"))
        {
            // the keys of the property map are the collection of property names
            return CurveLegendPropertiesMap.Keys;
        }

        // this is not my control
        throw new NotSupportedException();
    }

    // Get the property value by parsing the accessible description
    public override object GetPropertyValue(UITestControl uiTestControl, string propertyName)
    {
        if (String.Equals(propertyName, "State", StringComparison.OrdinalIgnoreCase))
        {
            object[] native = uiTestControl.NativeElement as object[];
            IAccessible acc = native[0] as IAccessible;

            string[] descriptionTokens = acc.accDescription.Split(new char[] { ';' });
            return descriptionTokens[1];
        }

        // this is not my control
        throw new NotSupportedException();
    }
    ```

5. 覆寫 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName>，以指出您的組件為您的控制項及其子系提供控制項特定的支援。

    ```csharp
    public override int GetControlSupportLevel(UITestControl uiTestControl)
    {
        // For MSAA, check the control type
        if (string.Equals(uiTestControl.TechnologyName, "MSAA",
            StringComparison.OrdinalIgnoreCase) &&
            (uiTestControl.ControlType == "Chart"||uiTestControl.ControlType == "Text"))
        {
            return (int)ControlSupport.ControlSpecificSupport;
        }

        // This is not my control, so return NoSupport
        return (int)ControlSupport.NoSupport;
    }
    ```

6. 覆寫 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName> 的其餘抽象方法。

    ```csharp
    public override string[] GetPredefinedSearchProperties(Type specializedClass)
    {
        throw new NotImplementedException();
    }

    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override void SetPropertyValue(UITestControl uiTestControl, string propertyName, object value)
    {
        throw new NotImplementedException();
    }

    public override string GetPropertyForAction(UITestControl uiTestControl, UITestAction action)
    {
        throw new NotImplementedException();
    }

    public override string[] GetPropertyForControlState(UITestControl uiTestControl, ControlStates uiState, out bool[] stateValues)
    {
        throw new NotImplementedException();
    }

    ```

7. 加入衍生自 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> 的擴充套件類別。

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        internal class ChartControlExtensionPackage : UITestExtensionPackage
        {
        }
    }
    ```

8. 定義組件的 `UITestExtensionPackage` 屬性。

    ```csharp
    [assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
                    "ChartControlExtensionPackage",
                    typeof(ChartControlExtensionPackage.ChartControlExtensionPackage))]
    namespace ChartControlExtensionPackage
    {
       …
    ```

9. 在擴充套件類別中，覆寫 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName>，以在要求屬性提供者時，傳回屬性提供者類別。

    ```csharp
    internal class ChartControlExtensionPackage : UITestExtensionPackage
    {
        public override object GetService(Type serviceType)
        {
            if (serviceType == typeof(UITestPropertyProvider))
            {
                if (propertyProvider == null)
                {
                    propertyProvider = new ChartControlPropertyProvider();
                }
                return propertyProvider;
            }
            return null;
        }

        private UITestPropertyProvider propertyProvider = null;
    }
    ```

10. 覆寫 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> 的其餘抽象方法和屬性。

    ```csharp

    public override void Dispose() { }

    public override string PackageDescription
    {
        get { return "Supports coded UI testing of ChartControl"; }
    }

    public override string PackageName
    {
        get { return "ChartControl Test Extension"; }
    }

    public override string PackageVendor
    {
        get { return "Microsoft (sample)"; }
    }

    public override Version PackageVersion
    {
        get { return new Version(1, 0); }
    }

    public override Version VSVersion
    {
        get { return new Version(10, 0); }
    }
    ```

11. 建置您的二進位檔，並將其複製到 **%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**。

> [!NOTE]
> 這個擴充套件將會套用至 "Text" 類型的任何控制項。 如果您要測試多個相同類型的控制項，您必須個別進行測試，並管理當您錄製測試時所要部署的擴充套件。

## <a name="codegeneration"></a> 藉由實作類別來存取自訂屬性，支援程式碼產生
 當自動程式碼 UI 測試產生器從工作階段錄製作業產生程式碼時，它會使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> 類別來存取您的控制項。

```csharp

      UITestControl uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.GetProperty("State").ToString());
```

 如果您已實作屬性提供者來提供控制項自訂屬性的存取權，您可以加入用來存取這些屬性的特定類別，如此可簡化所產生的程式碼。

```csharp

      ControlLegend uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.State);
```

### <a name="to-add-a-specialized-class-to-access-your-control"></a>加入用來存取控制項的特定類別
 ![CUIT&#95;CodeGen](../test/media/cuit-codegen.png "CUIT_CodeGen")

1. 實作衍生自 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> 的類別，並將控制項的類型加入建構函式中的搜尋屬性集合。

    ```csharp
    public class CurveLegend:WinControl
    {
       public CurveLegend(UITestControl c) : base(c)
       {
          // The curve legend control is a “text” type of control
          SearchProperties.Add(
             UITestControl.PropertyNames.ControlType, "Text");
       }
    }
    ```

2. 實作控制項的自訂屬性，以做為類別的屬性。

    ```csharp
    public virtual string State
    {
        get
        {
            return (string)GetProperty("State");
        }
    }
    ```

3. 覆寫屬性提供者的 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> 方法，以針對曲線圖例子控制項，傳回新類別的類型。

    ```csharp
    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
       if (uiTestControl.ControlType.NameEquals("Text"))
       {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
          return typeof(CurveLegend);
       }

       // this is not a curve legend control
       return null;
    }
    ```

4. 覆寫屬性提供者的 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> 方法，以傳回新類別的 PropertyNames 方法的類型。

    ```csharp
    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Text"))
        {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
            return typeof(CurveLegend.PropertyNames);
        }

        // this is not a curve legend control
        return null;
    }
    ```

## <a name="intentawareactions"></a> 藉由實作動作篩選，支援意圖感知動作
 當 Visual Studio 錄製測試時，它會擷取每個滑鼠和鍵盤事件。 不過，在某些情況下，動作的意圖可能會在一系列的滑鼠和鍵盤事件中遺失。 比方說，如果您的控制項支援自動完成，在不同的環境中播放測試時，同一組滑鼠和鍵盤事件可能會導致不同的值。 您可以加入動作篩選外掛程式，將一系列鍵盤和滑鼠事件取代成單一動作。 如此一來，您就可以將導致選取某個值的一系列滑鼠和鍵盤事件，取代成設定該值的單一動作。 這麼做可防止自動程式碼 UI 測試在不同環境之間所產生的自動完成差異。

### <a name="to-support-intent-aware-actions"></a>支援意圖感知動作
 ![CUIT&#95;動作](../test/media/cuit-actions.png "CUIT_Actions")

1. 執行衍生自[microsoft.visualstudio.testtools.uitest.common.uitestactionfilter>](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))的動作篩選準則類別，並覆寫[ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29)、 [Category](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110))、 [Enabled](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110))、 [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110))、 [Group](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110))和[Name](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110))屬性。

    ```csharp
    internal class MyActionFilter : UITestActionFilter
    {
       // If the user actions we are aggregating exceeds the time allowed,
       // this filter is not applied. (The timeout is configured when the
       // test is run.)
       public override bool ApplyTimeout
       {
          get { return true; }
       }

       // Gets the category of this filter. Categories of filters
       // are applied in priority order.
       public override UITestActionFilterCategory Category
       {
          get { return UITestActionFilterCategory.PostSimpleToCompoundActionConversion; }
       }

       public override bool Enabled
       {
          get { return true; }
       }

       public override UITestActionFilterType FilterType
       {
          // This action filter operates on a single action
          get { return UITestActionFilterType.Unary; }
       }

       // Gets the name of the group to which this filter belongs.
       // A group can be enabled/disabled using configuration file.
       public override string Group
       {
          get { return "ChartControlActionFilters"; }
       }

       // Gets the name of this filter.
       public override string Name
       {
          get { return "Convert Double-Click to Single-Click"; }
       }
    ```

2. 覆寫 `UITestActionFilter.ProcessRule`。 此範例會將按兩下動作取代成按一下動作。

    ```csharp
    public override bool ProcessRule(IUITestActionStack actionStack)
    {
        if (actionStack.Count > 0)
        {
            MouseAction lastAction = actionStack.Peek() as MouseAction;
            if (lastAction != null)
            {
                if (lastAction.UIElement.ControlTypeName.Equals(
                     ControlType.Text.ToString(),
                     StringComparison.OrdinalIgnoreCase))
                {
                    if(lastAction.ActionType == MouseActionType.DoubleClick)
                    {
                        // Convert to single click
                        lastAction.ActionType = MouseActionType.Click;
                    }
                }
            }
        }
        // Do not stop aggregation
        return false;
    }
    ```

3. 將動作篩選加入擴充套件的 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> 方法。

    ```csharp
    public override object GetService(Type serviceType)
    {
       if (serviceType == typeof(UITestPropertyProvider))
       {
          if (propertyProvider == null)
          {
             propertyProvider = new PropertyProvider();
          }
          return propertyProvider;
       }
       else if (serviceType == typeof(UITestActionFilter))
       {
          if (actionFilter == null)
          {
             actionFilter = new RadGridViewActionFilter();
          }
          return actionFilter;
       }
       return null;
    }
    ```

4. 建置您的二進位檔，並將其複製到 %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages。

> [!NOTE]
> 動作篩選與協助工具實作或屬性提供者沒有相依關係。

## <a name="debug-your-property-provider-or-action-filter"></a>偵錯屬性提供者或動作篩選
 內容提供者和動作篩選會在一個擴充套件中實作，自動程式碼 UI 測試產生器會在不同於您的應用程式的個別處理序中，載入及執行此擴充套件。

#### <a name="to-debug-your-property-provider-or-action-filter"></a>偵錯內容提供者或動作篩選

1. 建置延伸模組套件的偵錯版本，將 .dll 和.pdb 檔案複製到 %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages。

2. 執行您的應用程式 (不在偵錯工具中)。

3. 執行自動程式碼 UI 測試產生器。

     `codedUITestBuilder.exe  /standalone`

4. 將偵錯工具附加至 codedUITestBuilder 處理序。

5. 在您的程式碼中設定中斷點。

6. 在自動程式碼 UI 測試產生器中，建立判斷提示來運作您的屬性提供者，並錄製動作來運作您的動作篩選。

## <a name="external-resources"></a>外部資源

### <a name="guidance"></a>指引
 [使用 Visual Studio 2012 測試持續傳遞 - 第 2 章：單元測試：測試內部](https://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.AccessibleObject>
- [使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)
