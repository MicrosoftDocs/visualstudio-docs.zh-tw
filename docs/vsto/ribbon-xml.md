---
title: 功能區 XML
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c93553535ca85f63db64be773afa76711a38359b
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693126"
---
# <a name="ribbon-xml"></a>功能區 XML
  功能區 (XML) 項目可讓您使用 XML 自訂功能區。 如果您想要自訂功能區的功能區 （視覺化設計工具） 項目不支援的方式，請使用功能區 (XML) 項目。 您可以如何處理每個項目比較，請參閱[功能區概觀](../vsto/Ribbon-overview.md)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="add-a-ribbon-xml-item-to-a-project"></a>將功能區 (XML) 項目加入至專案  
 您可以從 [加入新項目] **ribbon** 對話方塊，將 [功能區 (XML)] **GetCustomUI** 項目加入至任何 Office 專案。 Visual Studio 會自動將下列檔案加入您的專案中：  
  
-   功能區 XML 檔。 這個檔案會定義功能區使用者介面 (UI)。 請使用這個檔案加入 UI 項目，例如索引標籤、群組和控制項。 如需詳細資訊，請參閱[功能區 XML 檔案參考](#RibbonDescriptorFile)本主題稍後。  
  
-   功能區程式碼檔案。 此檔案內含「功能區類別」 *GetCustomUI*(ribbon class)。 這個類別具有您在 [加入新項目] **ribbon** 對話方塊中為 [功能區 (XML)] **GetCustomUI** 項目所指定的名稱。 Microsoft Office 應用程式會使用這個類別的執行個體，來載入自訂功能區。 如需詳細資訊，請參閱[功能區類別參考](#RibbonExtensionClass)本主題稍後。  
  
 根據預設，這些檔案會加入自訂群組**增益集**功能區中的索引標籤。  
  
## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>在 Microsoft Office 應用程式中顯示自訂功能區  
 您將加入之後**功能區 (XML)** 項目至專案，您必須將程式碼加入**ThisAddin**， **ThisWorkbook**，或**ThisDocument**類別會覆寫`CreateRibbonExtensibilityObject`方法，並將功能區 XML 類別傳回 Office 應用程式。  
  
 下列程式碼範例將覆寫 `CreateRibbonExtensibilityObject` 方法並傳回名為 MyRibbon 的功能區 XML 類別。  
  
 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
## <a name="define-the-behavior-of-the-custom-ribbon"></a>定義自訂功能區的行為  
 您可以回應使用者動作，例如按一下功能區上的按鈕，藉由建立*回呼方法*。 回呼方法和 Windows Forms 控制項中的事件非常類似，但回呼方法是由 UI 項目中 XML 的屬性所識別。 請在功能區類別中撰寫方法，接著控制項便會呼叫與屬性值名稱相同的方法。 例如，您可以建立使用者按一下功能區上的按鈕時呼叫的回呼方法。 建立回呼方法需要執行兩個步驟：  
  
-   在程式碼中識別回呼方法的功能區 XML 檔案中，將屬性指派給控制項。  
  
-   在功能區類別中定義回呼方法。  
  
> [!NOTE]  
>  Outlook 還需要另一個步驟。 如需詳細資訊，請參閱[outlook 自訂功能區](../vsto/customizing-a-ribbon-for-outlook.md)。  
  
 如需示範如何自動從功能區應用程式的逐步解說，請參閱[逐步解說： 使用功能區 XML 建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)。  
  
### <a name="assign-callback-methods-to-controls"></a>將回呼方法指派給控制項  
 若要將回呼方法指派給功能區 XML 檔中的控制項，請加入指定回呼方法類型及方法名稱的屬性。 例如，下列項目會定義擁有名為 **ribbon** 之 `OnToggleButton1`。  
  
```xml  
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />  
```  
  
 當使用者執行與特定控制項相關聯的主要工作時，便會呼叫**GetCustomUI** 。 例如，當使用者按一下切換按鈕時，便會呼叫該按鈕的 **GetCustomUI** 回呼方法。  
  
 您在屬性中指定的方法可以具有任何名稱。 但必須符合您在功能區程式碼檔案中定義之方法的名稱。  
  
 您可以將許多不同類型的回呼方法指定給功能區控制項。 如需每個控制項可用之回呼方法的完整清單，請參閱技術文件[自訂 Office (2007) 功能區使用者介面開發人員 (組件 3 之 3)](http://msdn.microsoft.com/en-us/a16c7df5-93f3-4920-baa8-7b7290794c15)。  
  
###  <a name="CallBackMethods"></a> 定義回呼方法  
 請在功能區程式碼檔案的功能區類別中定義回呼方法。 回呼方法具有幾項需求：  
  
-   必須將其宣告為公用。  
  
-   其名稱必須符合您指派給功能區 XML 檔中控制項之回呼方法的名稱。  
  
-   其簽章必須符合相關功能區項目適用之回呼方法類型的簽章。  
  
 如需功能區控制項回呼方法簽章的完整清單，請參閱技術文件[自訂 Office (2007) 功能區使用者介面開發人員 (組件 3 之 3)](http://msdn.microsoft.com/en-us/a16c7df5-93f3-4920-baa8-7b7290794c15)。 Visual Studio 不會針對您在功能區程式碼檔案中建立的回呼方法提供 IntelliSense 支援。 如果您建立的回呼方法不符合有效的簽章，雖然程式碼會進行編譯，但是當使用者按一下控制項時，並不會產生任何反應。  
  
 所有的回呼方法都有 <xref:Microsoft.Office.Core.IRibbonControl> 參數，代表呼叫該方法的控制項。 您可以使用這個參數，對多個控制項重複使用相同的回呼方法。 下列程式碼範例示範的 **GetCustomUI** 回呼方法會根據使用者所按下的控制項，執行不同的工作。  
  
 [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
 [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]  
  
##  <a name="RibbonDescriptorFile"></a> 功能區 XML 檔案參考  
 您可以定義自訂功能區加入項目和屬性的功能區 XML 檔案。 根據預設，功能區 XML 檔包含下列 XML。  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">  
  <ribbon>  
    <tabs>  
      <tab idMso="TabAddIns">  
        <group id="MyGroup"  
               label="My Group">  
        </group>  
      </tab>  
    </tabs>  
  </ribbon>  
</customUI>  
```  
  
 下表描述功能區 XML 檔中的預設項目。  
  
|元素|描述|  
|-------------|-----------------|  
|**customUI**|代表 VSTO 增益集專案中的自訂功能區。|  
|**ribbon**|代表功能區。|  
|**索引標籤**|代表一組功能區索引標籤。|  
|**索引標籤**|代表單一功能區索引標籤。|  
|**group**|代表功能區索引標籤上的控制項群組。|  
  
 這些項目有指定的外觀和行為的自訂功能區的屬性。 下表描述功能區 XML 檔中的預設屬性。  
  
|屬性|父項目|描述|  
|---------------|--------------------|-----------------|  
|**onLoad**|**customUI**|識別應用程式載入功能區時所呼叫的方法。|  
|**idMso**|**索引標籤**|識別要顯示在功能區中的內建索引標籤。|  
|**id**|**group**|識別群組。|  
|**標籤**|**group**|指定出現在群組上的文字。|  
  
 功能區 XML 檔案中的預設項目和屬性是可用項目和屬性的小型子集。 如需可用的項目和屬性的完整清單，請參閱技術文件[自訂 Office (2007) 功能區使用者介面開發人員 (第 3 的第 2 部分)](http://msdn.microsoft.com/en-us/6b904f55-525f-4520-9b81-a017db65657b)。  
  
##  <a name="RibbonExtensionClass"></a> 功能區類別參考  
 Visual Studio 會在功能區程式碼檔中產生功能區類別。 將功能區上控制項的回呼方法加入這個類別。 這個類別會實作 <xref:Microsoft.Office.Core.IRibbonExtensibility> 介面。  
  
 下表描述此類別中的預設方法。  
  
|方法|描述|  
|------------|-----------------|  
|`GetCustomUI`|傳回功能區 XML 檔案的內容。 Microsoft Office 應用程式呼叫此方法來取得 XML 字串，定義自訂功能區使用者介面。 這個方法會實作 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> 方法。 **注意：** `GetCustomUI`應該只能為傳回功能區 XML 檔案的內容而實作不應該用來初始化 VSTO 增益集。 具體而言，您不應嘗試在 `GetCustomUI` 實作中顯示對話方塊或其他視窗。 否則自訂功能區可能無法正確運作。 如果需要執行初始化 VSTO 增益集的程式碼，請將該程式碼加入至 `ThisAddIn_Startup` 事件處理常式。|  
|`OnLoad`|將 <xref:Microsoft.Office.Core.IRibbonControl> 參數指派給 `Ribbon` 欄位。 Microsoft Office 應用程式會呼叫這個方法，當它們載入自訂功能區。 您可以使用此欄位來動態更新的自訂功能區。 如需詳細資訊，請參閱技術文件[自訂 Office (2007) 功能區使用者介面開發人員 (第 3 的第 1 部分)](http://msdn.microsoft.com/en-us/a4fd6d18-d4a8-4e64-bd89-f437208573d3)。|  
|`GetResourceText`|由 `GetCustomUI` 方法呼叫以取得功能區 XML 檔案的內容。|  
  
## <a name="see-also"></a>另請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [逐步解說： 使用功能區 XML 建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)  
  
  