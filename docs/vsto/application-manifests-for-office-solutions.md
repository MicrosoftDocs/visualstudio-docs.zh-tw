---
title: "Office 方案的應用程式資訊清單 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: application manifests [Office development in Visual Studio]
ms.assetid: dd38685f-f429-4a35-8c11-a03372c9770a
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: feda5cbd710ad1d3b7175219261a16f78a774f7d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="application-manifests-for-office-solutions"></a>Office 方案的應用程式資訊清單
  應用程式資訊清單是描述載入至 Microsoft Office 方案之組件的 XML 檔案。 Visual Studio 中的 Microsoft Office Development Tools 會使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 參考中定義的 [ndptecclick](/visualstudio/deployment/clickonce-application-manifest) 應用程式資訊清單結構描述。  
  
 Office 方案的應用程式資訊清單會使用下列 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 項目和屬性。  
  
|項目|描述|屬性|  
|-------------|-----------------|----------------|  
|[&#60; 組件 &#62;元素 &#40;ClickOnce 應用程式 &#41;](/visualstudio/deployment/assembly-element-clickonce-deployment)|必要項。 最上層項目。|`manifestVersion`|  
|[&#60; assemblyIdentity &#62;元素 &#40;ClickOnce 應用程式 &#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment)|必要項。 識別 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 應用程式的主要組件。|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[&#60; trustInfo &#62;元素 &#40;ClickOnce 應用程式 &#41;](/visualstudio/deployment/trustinfo-element-clickonce-application)|識別應用程式安全性需求。|無|  
|[&#60; 進入點 &#62;元素 &#40;ClickOnce 應用程式 &#41;](/visualstudio/deployment/entrypoint-element-clickonce-application)|必要項。 識別執行的應用程式程式碼進入點。|`name`<br /><br /> `dependencyName`<br /><br /> `customHostSpecified`|  
|[&#60; 相依性 &#62;元素 &#40;ClickOnce 應用程式 &#41;](/visualstudio/deployment/dependency-element-clickonce-deployment)|必要項。 識別執行應用程式所需的每個相依性。 選擇性地識別需要預先安裝的組件。|無|  
|[&#60; 檔案 &#62;元素 &#40;ClickOnce 應用程式 &#41;](/visualstudio/deployment/file-element-clickonce-application)|必要項。 識別應用程式所使用的每個非組件檔案。 可以包含與檔案相關聯的元件物件模型 (COM) 隔離資料。|`name`<br /><br /> `size`|  
  
 Office 方案的應用程式資訊清單在 `co.v1` 命名空間中具有下列項目。  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>   
```  
  
 這些應用程式資訊清單在 `vstav3` 命名空間中也具有下列項目和屬性。  
  
```  
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
  
|項目|描述|屬性|  
|-------------|-----------------|----------------|  
|[&#60; customHostSpecified &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|必要項。 將資訊清單特別標示為 Office 方案。|無|  
|[&#60; 增益集 &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/addin-element-office-development-in-visual-studio.md)|必要項。 將進入點儲存至單一命名空間。|無|  
|[&#60; entryPointsCollection &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|必要項。 群組一或多個 Office 方案的所有組件。|`id`|  
|[&#60; 進入點 &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/entrypoints-element-office-development-in-visual-studio.md)|必要項。 群組所有組件以執行 Office 方案。|無|  
|[&#60; 進入點 &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/entrypoint-element-office-development-in-visual-studio.md)|必要項。 識別要在 Office 方案中執行的組件。|`class`<br /><br /> `contract`|  
|[&#60; update &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/update-element-office-development-in-visual-studio.md)|必要項。 設定方案的更新。|`enabled`<br /><br /> `expiration`|  
|[&#60; postActions &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/postactions-element-office-development-in-visual-studio.md)|選擇項。 群組在安裝 Office 方案後執行的所有部署後動作。|無|  
|[&#60; postAction &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/postaction-element-office-development-in-visual-studio.md)|選擇項。 識別部署後動作。|無|  
|[&#60; postActionData &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/postactiondata-element-office-development-in-visual-studio.md)|選擇項。 設定部署後動作的資料。|無|  
|[&#60; 應用程式 &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/application-element-office-development-in-visual-studio.md)|必要項。 將應用程式特定資訊包裝成單一節點。|無|  
|[&#60; 自訂 &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/customizations-element-office-development-in-visual-studio.md)|必要項。 將所有應用程式主機特定資訊儲存至不同的命名空間。|無|  
|[&#60; 自訂 &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/customization-element-office-development-in-visual-studio.md)|必要項。 將應用程式主機特定資訊儲存至不同的命名空間。|`xmlns`|  
|[&#60; 文件 &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/document-element-office-development-in-visual-studio.md)|只有文件層級方案才需要。 儲存自訂特定資訊。|`solutionId`|  
|[&#60; appAddin &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/appaddin-element-office-development-in-visual-studio.md)|只有應用程式層級方案才需要。 儲存自訂特定資訊。|`application`<br /><br /> `loadBehavior`<br /><br /> `keyName`|  
|[&#60; friendlyName &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/friendlyname-element-office-development-in-visual-studio.md)|選擇項。 儲存出現在已安裝之 VSTO 增益集清單中的 VSTO 增益集名稱。|無|  
|[&#60; 描述 &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/description-element-office-development-in-visual-studio.md)|只有 VSTO 增益集才需要。儲存出現在已安裝之程式清單中的描述。|無|  
|[&#60; formRegions &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/formregions-element-office-development-in-visual-studio.md)|只有包含表單區域的 Outlook VSTO 增益集才需要。|無|  
|[&#60; formRegion &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/formregion-element-office-development-in-visual-studio.md)|只有包含表單區域的 Outlook VSTO 增益集才需要。|`Name`|  
|[&#60; vstoRuntime &#62;元素 &#40; Visual Studio &#41; 中的 Office 程式開發](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|必要項。 描述 Office 方案支援的特定 Visual Studio Tools for Office Runtime 版本。|`release`<br /><br /> `version`<br /><br /> `supportUrl`|  
  
## <a name="remarks"></a>備註  
 您可以手動編輯 Office 方案中的應用程式和部署資訊清單。 之後必須使用資訊清單產生和編輯工具 (mage.exe 和 mageui.exe)，重新簽署應用程式和部署資訊清單。 如需詳細資訊，請參閱 [How to: Re-sign Application and Deployment Manifests](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests)。  
  
## <a name="file-location"></a>檔案位置  
 每個方案版本都會有特定的應用程式資訊清單。 因此，應用程式資訊清單應該與部署資訊清單分開儲存。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將版本特定檔案，放在以發行資料夾之 [應用程式檔案]  子目錄中相關聯版本命名的子目錄中。  
  
## <a name="file-name-syntax"></a>檔名語法  
 應用程式資訊清單檔案的名稱應該是 `assemblyIdentity` 項目中識別的應用程式完整名稱和副檔名，後面接著副檔名 .manifest。 例如，參考 OutlookAddIn1.dll 自訂的應用程式資訊清單會使用下列檔案名稱語法。  
  
 `OutlookAddIn1.dll.manifest`  
  
## <a name="see-also"></a>另請參閱  
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  