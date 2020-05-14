---
title: 如何:為專用庫創建 Atom 源 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72fbf2d3973ffd84de1cf6f33788c43511c3ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711003"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>如何:為專用函式庫建立 Atom 源
您可以建立 Atom (RSS) 來源到包含延伸的 Intranet 位置,並將來源為專用函式庫加入**到擴充與更新**。 有關詳細資訊,請參閱[私人畫廊](../extensibility/private-galleries.md)。

## <a name="create-an-atom-feed"></a>建立原子來源
 要將 Atom 源建立為專用庫,請首先將擴展名 *(.vsix*檔)收集到資料夾中。 如果需要,可以將它們組織到子資料夾中。 您還需要以下資源:

- 使擴展作為專用庫可用的*atom.xml*檔。 有關如何將*Atom.xml*檔案連接到**延伸和更新**的資訊,請參閱[專用函式庫](../extensibility/private-galleries.md)。

- 包含從副檔名中提取的任何影像檔的資料夾(例如,螢幕截圖)。 *Atom.xml*檔包含指向這些圖像的相對連結,以便它們在**擴展和更新**中可用。

  例如,假設您已將以下兩個擴展收集到一個資料夾中:

- *Template_Wizard_239.vsix*,這是一個空的 VSIX 專案範本。

- *選擇高亮顯示.vsix*, 這是一個突出顯示選定單詞的所有實例的工具。

  *atom.xml*檔案的內容類似於以下範例:

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

 請注意,兩個鏈接標記是指生成的圖像資料夾中的屏幕截圖。

## <a name="see-also"></a>另請參閱
- [私人畫廊](../extensibility/private-galleries.md)
