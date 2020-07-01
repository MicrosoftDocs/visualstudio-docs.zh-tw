---
title: Office 方案的應用程式資訊清單
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a6272f145ee2c7ef2a91cc635112e440e6404457
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531504"
---
# <a name="application-manifests-for-office-solutions"></a>Office 方案的應用程式資訊清單
  應用程式資訊清單是描述載入至 Microsoft Office 方案之組件的 XML 檔案。 中的 Microsoft Office 開發工具 Visual Studio 使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)參考中定義的應用程式資訊清單架構。

 Office 方案的應用程式資訊清單會使用下列 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 項目和屬性。

|元素|描述|屬性|
|-------------|-----------------|----------------|
|[&#60;元件&#62; 元素 &#40;ClickOnce 應用程式&#41;](../deployment/assembly-element-clickonce-deployment.md)|必要。 最上層項目。|**manifestVersion**|
|[&#60;assemblyIdentity&#62; 元素 &#40;ClickOnce 應用程式&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|必要。 識別 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 應用程式的主要組件。|**name**<br /><br /> **version**<br /><br /> **公開金鑰**<br /><br /> **processorArchitecture**<br /><br /> **語言**|
|[&#60;trustInfo&#62; 元素 &#40;ClickOnce 應用程式&#41;](../deployment/trustinfo-element-clickonce-application.md)|識別應用程式安全性需求。|None|
|[&#60;entryPoint&#62; 元素 &#40;ClickOnce 應用程式&#41;](../deployment/entrypoint-element-clickonce-application.md)|必要。 識別執行的應用程式程式碼進入點。|**name**<br /><br /> **dependencyName**<br /><br /> **d**|
|[&#60;相依性&#62; 元素 &#40;ClickOnce 應用程式&#41;](../deployment/dependency-element-clickonce-deployment.md)|必要。 識別執行應用程式所需的每個相依性。 選擇性地識別需要預先安裝的組件。|None|
|[&#60;檔案&#62; 元素 &#40;ClickOnce 應用程式&#41;](../deployment/file-element-clickonce-application.md)|必要。 識別應用程式所使用的每個非組件檔案。 可以包含與檔案相關聯的元件物件模型 (COM) 隔離資料。|**name**<br /><br /> **size**|

 Office 方案的應用程式資訊清單在 `co.v1` 命名空間中具有下列項目。

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

 這些應用程式資訊清單在 `vstav3` 命名空間中也具有下列項目和屬性。

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customizations>
      <customization>
      </customization>
    </customizations>
  </application
</addIn>
```

|元素|描述|屬性|
|-------------|-----------------|----------------|
|[&#60;d&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|必要。 將資訊清單特別標示為 Office 方案。|None|
|[&#60;增益集&#62; 元素 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|必要。 將進入點儲存至單一命名空間。|None|
|[&#60;entryPointsCollection&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|必要。 群組一或多個 Office 方案的所有組件。|**id**|
|[&#60;e&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|必要。 群組所有組件以執行 Office 方案。|None|
|[&#60;進入點&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|必要。 識別要在 Office 方案中執行的組件。|**class**<br /><br /> **協定**|
|[&#60;更新&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/update-element-office-development-in-visual-studio.md)|必要。 設定方案的更新。|**後**<br /><br /> **expiration**|
|[&#60;P s&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|選擇性。 群組在安裝 Office 方案後執行的所有部署後動作。|None|
|[&#60;P n&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|選擇性。 識別部署後動作。|None|
|[&#60;postActionData&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|選擇性。 設定部署後動作的資料。|None|
|[&#60;應用程式&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/application-element-office-development-in-visual-studio.md)|必要。 將應用程式特定資訊包裝成單一節點。|None|
|[&#60;自訂&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|必要。 將所有應用程式主機特定資訊儲存至不同的命名空間。|None|
|[&#60;自訂&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|必要。 將應用程式主機特定資訊儲存至不同的命名空間。|**xmlns**|
|[&#60;檔&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/document-element-office-development-in-visual-studio.md)|只有文件層級方案才需要。 儲存自訂特定資訊。|**solutionId**|
|[&#60;appAddin&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|只有應用程式層級方案才需要。 儲存自訂特定資訊。|**應用程式**<br /><br /> **loadBehavior**<br /><br /> **名**|
|[&#60;friendlyName&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|選擇性。 儲存出現在已安裝之 VSTO 增益集清單中的 VSTO 增益集名稱。|None|
|[&#60;描述&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/description-element-office-development-in-visual-studio.md)|只有 VSTO 增益集才需要。會儲存已安裝的程式清單中所顯示的描述。|None|
|[&#60;F s&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|只有包含表單區域的 Outlook VSTO 增益集需要。|None|
|[&#60;formRegion&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|只有包含表單區域的 Outlook VSTO 增益集需要。|**名稱**|
|[&#60;V m e&#62; 元素 &#40;Visual Studio 中的 Office 開發&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|必要。 描述 Office 方案支援的特定 Visual Studio Tools for Office Runtime 版本。|**版本**<br /><br /> **version**<br /><br /> **supportUrl**|

## <a name="remarks"></a>備註
 您可以手動編輯 Office 方案中的應用程式和部署資訊清單。 之後，您必須使用資訊清單產生和編輯工具（*mage.exe*和*mageui.exe*）重新簽署應用程式和部署資訊清單。 如需詳細資訊，請參閱[如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)。

## <a name="file-location"></a>檔案位置
 每個方案版本都會有特定的應用程式資訊清單。 因此，應用程式資訊清單應該與部署資訊清單分開儲存。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]會將版本特定檔案放在 [發行] 資料夾之 [*應用程式檔*] 子目錄中的相關聯版本所命名的子目錄中。

## <a name="file-name-syntax"></a>檔案名稱語法
 應用程式資訊清單檔案的名稱應該是**assemblyIdentity**元素中所識別之應用程式的完整名稱和副檔名，後面接著副檔名 *.manifest*。 例如，參考*OutlookAddIn1.dll*自訂的應用程式資訊清單會使用下列檔案名語法。

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>另請參閱

- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)