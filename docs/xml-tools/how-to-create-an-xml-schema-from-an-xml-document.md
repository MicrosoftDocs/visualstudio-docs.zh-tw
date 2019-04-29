---
title: 建立 XML 結構描述
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e93155f230ee4a564116f5d1357a97923706c36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783489"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>HOW TO：從 XML 文件建立 XML 結構描述

XML 編輯器可讓您從 XML 文件建立 XML 結構描述定義語言 (XSD) 結構描述。 XML 檔案會決定如何產生結構描述是以下列方式：

- 如果 XML 文件沒有結構描述或與其相關聯的「文件類型定義 (DTD)」，則會使用 XML 文件中的資料來推斷新的 XML 結構描述。

- 如果 XML 文件包含相關聯的 DTD，則外部 DTD 及內部子集將轉換成相對應的 XML 結構描述。

- 如果 XML 文件包含內嵌 XML 資料精簡 (XDR) 結構描述，則 XDR 結構描述會轉換成相對應的 XML 結構描述。

所建立的結構描述然後用來提供 IntelliSense XML 檔案中。

如需有關結構描述推斷引擎的詳細資訊，請參閱 <<c0> [ 推斷 XML 結構描述](/dotnet/standard/data/xml/inferring-an-xml-schema)。

## <a name="to-create-an-xml-schema"></a>建立 XML 結構描述

1. Visual Studio 中開啟 XML 檔案。

2. 在功能表列上選擇  **XML** > **Create Schema**。

   建立及開啟 XML 檔案中找到每個命名空間的 XML 結構描述文件。 每個結構描述會當作暫時的其他檔案開啟。 結構描述可儲存至磁碟、加入至專案或捨棄。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)