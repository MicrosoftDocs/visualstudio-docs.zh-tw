---
title: 建立 XML 架構
description: 瞭解如何使用 Visual Studio 中的 XML 編輯器，從 XML 檔建立 XML 架構定義語言 (XSD) 架構。
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e33a4add7ebc6a3e323331731f3183d7a0dce26f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970279"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>如何：從 XML 檔建立 XML 架構

XML 編輯器可讓您從 XML 檔建立 XML 架構定義語言 (XSD) 架構。 XML 檔案會決定如何以下列方式產生架構：

- 如果 XML 文件沒有結構描述或與其相關聯的「文件類型定義 (DTD)」，則會使用 XML 文件中的資料來推斷新的 XML 結構描述。

- 如果 XML 文件包含相關聯的 DTD，則外部 DTD 及內部子集將轉換成相對應的 XML 結構描述。

- 如果 XML 文件包含內嵌 XML 資料精簡 (XDR) 結構描述，則 XDR 結構描述會轉換成相對應的 XML 結構描述。

接著會使用所建立的架構，為 XML 檔案提供 IntelliSense。

如需架構推斷引擎的詳細資訊，請參閱 [推斷 XML 架構](/dotnet/standard/data/xml/inferring-an-xml-schema)。

## <a name="to-create-an-xml-schema"></a>建立 XML 結構描述

1. 在 Visual Studio 中開啟 XML 檔案。

2. 在功能表列上，選擇 [ **XML**  >  **建立架構**]。

   系統會為 XML 檔案中找到的每個命名空間建立並開啟 XML 架構檔。 每個結構描述會當作暫時的其他檔案開啟。 結構描述可儲存至磁碟、加入至專案或捨棄。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)
