---
title: Office 方案的應用程式資訊清單
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9665be31a59de33713f981889bc8cb8a8cb55eea
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248172"
---
# <a name="application-manifests-for-office-solutions"></a>Office 方案的應用程式資訊清單
  應用程式資訊清單是描述載入至 Microsoft Office 方案之組件的 XML 檔案。 Microsoft Office 開發工具，在 Visual Studio 中的使用[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]應用程式資訊清單結構描述中定義[ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)參考。  
  
 Office 方案的應用程式資訊清單會使用下列 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 項目和屬性。  
  
|元素|描述|屬性|  
|-------------|-----------------|----------------|  
|[&#60;組件&#62;項目&#40;ClickOnce 應用程式&#41;](/visualstudio/deployment/assembly-element-clickonce-deployment)|必要項。 最上層項目。|**manifestVersion**|  
|[&#60;組件識別&#62;項目&#40;ClickOnce 應用程式&#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment)|必要項。 識別 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 應用程式的主要組件。|**name**<br /><br /> **version**<br /><br /> **publicKeyToken**<br /><br /> **ProcessorArchitecture**<br /><br /> **language**|  
|[&#60;trustInfo&#62;項目&#40;ClickOnce 應用程式&#41;](/visualstudio/deployment/trustinfo-element-clickonce-application)|識別應用程式安全性需求。|無|  
|[&#60;entryPoint&#62;項目&#40;ClickOnce 應用程式&#41;](/visualstudio/deployment/entrypoint-element-clickonce-application)|必要項。 識別執行的應用程式程式碼進入點。|**name**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|  
|[&#60;相依性&#62;項目&#40;ClickOnce 應用程式&#41;](/visualstudio/deployment/dependency-element-clickonce-deployment)|必要項。 識別執行應用程式所需的每個相依性。 選擇性地識別需要預先安裝的組件。|無|  
|[&#60;檔案&#62;項目&#40;ClickOnce 應用程式&#41;](/visualstudio/deployment/file-element-clickonce-application)|必要項。 識別應用程式所使用的每個非組件檔案。 可以包含與檔案相關聯的元件物件模型 (COM) 隔離資料。|**name**<br /><br /> **size**|  
  
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
|[&#60;d&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|必要項。 將資訊清單特別標示為 Office 方案。|無|  
|[&#60;增益集&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|必要項。 將進入點儲存至單一命名空間。|無|  
|[&#60;entryPointsCollection&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|必要項。 群組一或多個 Office 方案的所有組件。|**id**|  
|[&#60;進入點&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|必要項。 群組所有組件以執行 Office 方案。|無|  
|[&#60;entryPoint&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|必要項。 識別要在 Office 方案中執行的組件。|**class**<br /><br /> **合約**|  
|[&#60;更新&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/update-element-office-development-in-visual-studio.md)|必要項。 設定方案的更新。|**enabled**<br /><br /> **到期日**|  
|[&#60;postActions&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|選擇性。 群組在安裝 Office 方案後執行的所有部署後動作。|無|  
|[&#60;postAction&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|選擇性。 識別部署後動作。|無|  
|[&#60;postActionData&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|選擇性。 設定部署後動作的資料。|無|  
|[&#60;應用程式&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/application-element-office-development-in-visual-studio.md)|必要項。 將應用程式特定資訊包裝成單一節點。|無|  
|[&#60;自訂&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|必要項。 將所有應用程式主機特定資訊儲存至不同的命名空間。|無|  
|[&#60;自訂&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|必要項。 將應用程式主機特定資訊儲存至不同的命名空間。|**xmlns**|  
|[&#60;文件&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/document-element-office-development-in-visual-studio.md)|只有文件層級方案才需要。 儲存自訂特定資訊。|**方案識別碼**|  
|[&#60;appAddin&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|只有應用程式層級方案才需要。 儲存自訂特定資訊。|**應用程式**<br /><br /> **LoadBehavior**<br /><br /> **keyName**|  
|[&#60;friendlyName&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|選擇性。 儲存出現在已安裝之 VSTO 增益集清單中的 VSTO 增益集名稱。|無|  
|[&#60;描述&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/description-element-office-development-in-visual-studio.md)|只有 VSTO 增益集才需要。儲存出現在已安裝之程式清單中的描述。|無|  
|[&#60;formRegions&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|只有包含表單區域的 Outlook VSTO 增益集才需要。|無|  
|[&#60;formRegion&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|只有包含表單區域的 Outlook VSTO 增益集才需要。|**名稱**|  
|[&#60;vstoRuntime&#62;項目&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|必要項。 描述 Office 方案支援的特定 Visual Studio Tools for Office Runtime 版本。|**release**<br /><br /> **version**<br /><br /> **supportUrl**|  
  
## <a name="remarks"></a>備註  
 您可以手動編輯 Office 方案中的應用程式和部署資訊清單。 之後，您必須重新簽署應用程式和部署資訊清單使用資訊清單產生和編輯工具 (*mage.exe*並*mageui.exe*)。 如需詳細資訊，請參閱[＜How to：重新簽署應用程式和部署資訊清單](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests)。  
  
## <a name="file-location"></a>檔案位置  
 每個方案版本都會有特定的應用程式資訊清單。 因此，應用程式資訊清單應該與部署資訊清單分開儲存。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將版本特定檔案，放在以發行資料夾之 [應用程式檔案]  子目錄中相關聯版本命名的子目錄中。  
  
## <a name="file-name-syntax"></a>檔案名稱語法  
 應用程式資訊清單檔案的名稱應該是完整名稱和應用程式的延伸模組中, 所指明**assemblyIdentity**項目，後面接著副檔名 *.manifest*。 比方說，是指應用程式資訊清單*OutlookAddIn1.dll*自訂會使用下列的檔案名稱語法。  
  
 `OutlookAddIn1.dll.manifest`  
  
## <a name="see-also"></a>另請參閱  
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  