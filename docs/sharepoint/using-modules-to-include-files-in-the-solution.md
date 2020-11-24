---
title: 使用模組來包含方案中的檔案 |Microsoft Docs
description: 使用模組或 SharePoint 方案中檔案的容器，將檔案部署至 SharePoint 伺服器，不論其檔案類型 (例如主版頁面) 。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aa0d6fe1855a1d60a0e1293e8422791f8148bd04
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442517"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>使用模組來包含方案中的檔案
  有時候您可能會想要將檔案部署至 SharePoint 伺服器，而不考慮其檔案類型，例如新的主版頁面。 若要這樣做，您可以使用 *模組* (不會與) 的程式 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 代碼模組混淆。 模組是 SharePoint 方案中檔案的容器。 部署方案時，模組中的檔案會複製到 SharePoint 伺服器上的指定資料夾中。

## <a name="module-items-and-elements"></a>模組專案和元素
 若要建立模組，請在 [ **加入新專案** ] 對話方塊中選擇它，將它加入至專案。 然後，修改其 *Elements.xml* 檔案，以包含您想要部署之檔案的名稱、在系統上的位置，以及應該將這些檔案複製到 SharePoint 伺服器上的位置。

 以下是模組的 *Elements.xml* 檔案範例：

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 新建立的模組包含下列預設檔案：

|檔案名稱|描述|
|---------------|-----------------|
|*Elements.xml*|模組的定義檔。|
|*Sample.txt*|預留位置檔案，作為模組中檔案的範例。|

 *Elements.xml* 檔案包含下列元素：

|元素名稱|描述|
|------------------|-----------------|
|元素|包含模組中定義的所有元素。|
|模組|Module 元素有單一屬性 *name*，可指定格式的模組名稱 `<Module Name="Module1">` 。<br /><br /> 請注意，如果您變更模組的名稱 (或其 *資料夾名稱* 屬性) ，您必須手動更新 module 元素中的名稱。<br /><br /> 如果您在 Module 元素中為檔案 (s) 指定子目錄， [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) 將會自動為其建立相符的目錄結構。|
|檔案|File 元素有兩個參數： *Path* 和 *Url*。<br /><br /> -Path： SharePoint 方案中檔案的名稱和位置。 格式為， `Path="Module1\Sample.txt"` 。<br /><br /> -Url：要將檔案部署到 SharePoint 伺服器上的位置。 格式為， `Url="Module1/Sample.txt"` 。<br /><br /> -Type：具有兩個設定的選擇性屬性： *GhostableInLibrary* 和 *Ghostable*。 格式為， `Type="GhostableInLibrary"` 。 指定 *GhostableInLibrary* 時，會將檔案新增至 SharePoint 中的文件庫，並在檔案新增至程式庫時連同清單專案一起加入。 指定 *Ghostable* 會導致將檔案新增至文件庫以外的 SharePoint。|

 您要部署的每個檔案都需要 `<File>` *Elements.xml* 中的個別元素專案。

## <a name="see-also"></a>另請參閱
- [如何：使用模組來包含檔案](../sharepoint/how-to-include-files-by-using-a-module.md)
- [如何：布建檔案](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [建立 SharePoint 的網頁元件](../sharepoint/creating-web-parts-for-sharepoint.md)
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
