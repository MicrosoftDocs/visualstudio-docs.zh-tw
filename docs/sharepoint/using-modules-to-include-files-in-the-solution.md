---
title: 使用模組來包含方案中的檔案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a9d8cf0da022c038c0e15e6b00f0bea0cdc3cef4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921545"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>使用模組來包含方案中的檔案
  可能有您可能的想要將檔案部署到 SharePoint 伺服器，不論他們的檔案類型，例如新的主版頁面。 若要這樣做，您可以使用*模組*(不到與混淆[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]的程式碼模組)。 模組是 SharePoint 方案中的檔案的容器。 部署方案時，模組中的檔案會複製到 SharePoint 伺服器上的指定資料夾中。  
  
## <a name="module-items-and-elements"></a>模組項目和項目
 若要建立模組，將它新增至專案中**加入新項目** 對話方塊。 然後，修改其*Elements.xml*檔案，以包含您想要部署，其中它們位於系統，而且它們應該複製到 SharePoint 伺服器上的檔案名稱。  
  
 以下是範例*Elements.xml*模組檔案：  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 新建立的模組包含下列的預設檔案：  
  
|檔案名稱|描述|  
|---------------|-----------------|  
|*Elements.xml*|模組定義檔。|  
|*Sample.txt*|預留位置檔案做為模組中的檔案的範例。|  
  
 *Elements.xml*檔案包含下列元素：  
  
|元素名稱|描述|  
|------------------|-----------------|  
|項目|包含所有模組中定義的項目。|  
|Module|Module 元素具有單一屬性，*名稱*，，指定模組的名稱格式`<Module Name="Module1">`。<br /><br /> 請注意，如果您變更模組的名稱 (或其*資料夾名稱*屬性)，您必須手動更新的模組項目中的名稱。<br /><br /> 如果您指定檔案的子目錄中的模組項目， [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) 會自動為它們建立相符的目錄結構。|  
|檔案|File 元素具有兩個參數，*路徑*並*Url*。<br /><br /> 路徑：名稱和位置的 SharePoint 方案中的檔案。 格式為， `Path="Module1\Sample.txt"`。<br /><br /> -Url:檔案在 SharePoint 伺服器的部署所在的位置。 格式為， `Url="Module1/Sample.txt"`。<br /><br /> 類型：選擇性屬性，有兩種設定：*GhostableInLibrary*並*Ghostable*。 格式為， `Type="GhostableInLibrary"`。 指定*GhostableInLibrary*表示檔案將會新增至 SharePoint 的文件庫與清單項目加入至程式庫時，伴隨著檔案。 指定*Ghostable*會導致要加入至 SharePoint 文件庫之外的檔案。|  
  
 您想要部署的每個檔案都需要個別`<File>`項目中的項目*Elements.xml*。  
  
## <a name="see-also"></a>另請參閱
 [如何：使用模組中包含的檔案](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [操作說明：佈建檔案](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [建立 SharePoint web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
