---
title: XML 結構描述
description: 深入瞭解 [XML 架構] 對話方塊，此對話方塊會用來選取要與 XML 檔產生關聯的 XML 架構定義語言 (XSD) 架構 () s。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1c91e97d0508ab85893409386ddd3ab9dded7f45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874830"
---
# <a name="xml-schemas-dialog-box"></a>XML 結構描述對話方塊

[ **Xml 架構** ] 對話方塊是用來選取要與 xml 檔相關聯的 xml 架構定義語言 (XSD) 架構 (s) 。 您可以從結構描述快取中選取結構描述，或指定快取中沒有的結構描述。 選取的結構描述會被視為結構描述集的一部分。 結構描述集用於 IntelliSense 以及 XML 文件驗證。

您可以按一下 [檔案屬性] 視窗上的 [**架構**] 按鈕，或從 [ **xml** ] 功能表選取 [**架構**]，來存取 [ **xml 架構**] 對話方塊。

## <a name="uielement-list"></a>UIElement 清單

**使用**

選取如何使用 XML 結構描述。

- **自動**： 目前的文件沒有使用這個結構描述，但是可用於自動關聯。 如果 XML 文件宣告符合此結構描述之 `targetNamespace` 的命名空間，將會自動關聯該結構描述，而且會包含在結構描述集中。

- **使用此架構**。 此結構描述正由目前的文件所使用。 使用者已經明確要求藉由按一下此結構描述來使用該結構描述，或者讓結構描述根據相符的 `targetNamespace` 自動關聯。

- **請勿使用選取的架構**。 即使結構描述擁有相符的 `targetNamespace`，目前的文件也不會使用此結構描述。 在結構描述快取或方案中有一個以上相同結構描述的版本時，這個設定對於解決衝突可能很實用。

**目標命名空間**

顯示與 XML 結構描述相關聯的目標命名空間。

**檔案名稱**

顯示 XML 結構描述檔案名稱。

**加入**

開啟 [ **開啟 XSD 架構** ] 對話方塊，可讓您選取要加入至架構集的其他架構。 當您將架構新增至架構集時，[ **使用** ] 資料行值會設定為 [ **使用此架構**]。

**移除**

從結構描述集移除目前選取的結構描述。 這樣會從記憶體中的結構描述快取 (但不會從檔案系統) 移除結構描述。

## <a name="see-also"></a>另請參閱

- [如何：選取要使用的 XML 架構](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [結構描述快取](../xml-tools/schema-cache.md)
