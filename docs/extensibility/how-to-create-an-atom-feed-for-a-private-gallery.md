---
title: 如何：建立私用資源庫的 Atom 摘要 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 269161e831fdb176dbfea844e951597efb467312
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905855"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>如何：建立私用資源庫的 Atom 摘要
您可以建立 Atom （RSS）摘要到包含延伸模組的內部網路位置，並將摘要新增至 [**擴充功能和更新**] 做為私用資源庫。 如需詳細資訊，請參閱私用資源[庫](../extensibility/private-galleries.md)。

## <a name="create-an-atom-feed"></a>建立 Atom 摘要
 若要建立 Atom 摘要做為私用資源庫，您必須先將延伸模組（*.vsix*檔案）收集到資料夾中。 如有需要，您可以將它們組織成子資料夾。 您也將需要下列資源：

- 可讓擴充功能當做私用資源庫使用的*atom.xml*檔案。 如需有關如何將*atom.xml*檔案連接到**擴充功能和更新**的詳細資訊，請參閱私用資源[庫](../extensibility/private-galleries.md)。

- 資料夾，其中包含從擴充功能（例如螢幕擷取畫面）解壓縮的任何影像檔案。 *atom.xml*檔案包含這些映射的相對連結，以便在 [**擴充功能和更新**] 中提供。

  例如，假設您已將下列兩個延伸模組收集到資料夾中：

- *Template_Wizard_239 .vsix*，這是空的 vsix 專案範本。

- *SelectionHighlight*，這是用來反白顯示所選單字之所有實例的工具。

  *atom.xml*檔案的內容會如下列範例所示：

```xml
<?xml version="1.0" encoding="UTF-8"?>
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
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
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

 請注意，這兩個連結標記會參考所產生之影像資料夾中的螢幕擷取畫面。

## <a name="see-also"></a>另請參閱
- [私用資源庫](../extensibility/private-galleries.md)
