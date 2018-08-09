---
title: 如何： 建立的 Atom 摘要私用組件庫 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0ea9df0bac68f9c16f5442d04fa4229f21bb29b2
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638488"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>如何： 建立私用組件庫摘要的 Atom
您可以建立 Atom (RSS) 到內部網路位置包含延伸模組，並加入至摘要**擴充功能和更新**為私用組件庫。 如需詳細資訊，請參閱 <<c0> [ 私用主機庫](../extensibility/private-galleries.md)。  
  
## <a name="create-an-atom-feed"></a>建立 Atom 摘要  
 若要建立的 Atom 摘要為私用組件庫，您先收集您的擴充功能 (*.vsix*檔案) 的資料夾。 您可以將它們組織到子資料夾如果您想要。 您也需要下列資源：  
  
-   *Atom.xml*為私用組件庫提供延伸模組的檔案。 如需有關如何連接資訊*atom.xml*的檔案**擴充功能和更新**，請參閱[私用主機庫](../extensibility/private-galleries.md)。  
  
-   包含任何擴充功能 （例如，螢幕擷取畫面） 從擷取的映像檔案的資料夾。 *Atom.xml*檔案會包含這些影像的相對連結，以便在有提供**擴充功能和更新**。  
  
 例如，假設您已收集下列兩個延伸模組到到資料夾：  
  
-   *Template_Wizard_239.vsix*，這是空的 VSIX 專案範本。  
  
-   *SelectionHighlight.vsix*，這是以反白顯示選取的字的所有執行個體的工具。  
  
 內容*atom.xml*檔案就會類似下列的範例：  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>   
<feed xmlns="http://www.w3.org/2005/Atom">  
<title type="text" />   
<id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
<updated>2011-04-14T21:25:48Z</updated>   
<entry>  
<id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
<title type="text">Highlight all occurrences of selected word</title>   
<summary type="text">This extends the editor to highlight ....</summary>   
<published>2011-04-14T14:24:51-07:00</published>   
<updated>2011-04-14T14:24:22-07:00</updated>   
<author>  
<name>Microsoft</name>   
</author>  
<link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
<link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
<content type="application/octet-stream" src="SelectionHighlight.vsix" />   
<Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
<Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
<Version>1.31</Version>   
<References />   
<Rating xsi:nil="true" />   
<RatingCount xsi:nil="true" />   
<DownloadCount xsi:nil="true" />   
</Vsix>  
</entry>  
<entry>  
<id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
...  
</entry>  
</feed>
```  
  
 請注意兩個連結標記是指產生資料夾中的映像的螢幕擷取畫面。  
  
## <a name="see-also"></a>另請參閱  
 [私用組件庫](../extensibility/private-galleries.md)
