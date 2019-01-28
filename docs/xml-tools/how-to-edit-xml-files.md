---
title: HOW TO：編輯 XML 檔案
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ee170d42390ed04292be28740dde4d597b7f7d9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005402"
---
# <a name="how-to-edit-xml-files"></a>HOW TO：編輯 XML 檔案

XML 編輯器是 XML 檔案的新編輯器。 它可用於獨立 XML 檔案或與 Visual Studio 專案相關的檔案上。 XML 編輯器是具有下列副檔名相關聯： *.config*， *.dtd*， *.xml*， *.xsd*， *.xdr*， *.xsl*， *.xslt*，和 *.vssettings*。 XML 編輯器也與未登錄特定編輯器，且包含 XML 或 DTD 內容的任何其他檔案類型相關聯。

> [!NOTE]
> HTML 編輯器可處理 XHTML 文件。

## <a name="to-edit-an-xml-file"></a>編輯 XML 檔案

1.  按兩下要編輯的檔案。

### <a name="to-add-a-new-xml-file-to-a-project"></a>將新的 XML 檔案加入至專案

1.  從**專案**功能表上，選取**加入新項目**。

2.  選取  **XML 檔案**從**範本**窗格。

3.  輸入中的檔案名稱**名稱**欄位，然後按**新增**。

     將 XML 檔案加入至專案，並在 XML 編輯器中開啟它。 檔案包含預設的 XML 宣告，`<?xml version="1.0" encoding="utf-8" ?>`。

## <a name="to-add-an-existing-xml-file-to-a-project"></a>將現有 XML 檔案加入至專案

1.  從**專案**功能表上，選取**加入現有項目**。

     **加入現有項目** 對話方塊隨即出現。

2.  選取 XML 檔案並按**新增**。

## <a name="to-create-a-new-xml-or-xslt-file"></a>建立新的 XML 或 XSLT 檔

1.  從**檔案**功能表上，選取**新增**。

     **新的檔案** 對話方塊隨即出現。

2.  選取  **XML 檔案**來建立新的 XML 檔案; 或者，選取**XSLT 檔**來建立新的 XSLT 樣式表。

3.  按一下 [開啟]。

## <a name="to-create-a-project-for-xml-files"></a>建立 XML 檔案的專案

1.  從**檔案**功能表上，選取**新增**，然後選取**專案**。

     [ **新增專案** ] 對話方塊隨即出現。

2.  選取您的選擇，選取的程式碼語言**空專案**，然後按一下**確定**。

3.  將 XML 檔案加入至專案。

     XML 編輯器會找到加入至此專案的結構描述，並在此專案開啟時編輯的任何 XML、結構描述或 XSLT 檔案中使用它們進行驗證及 IntelliSense。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)
- [屬性視窗、 XML 文件屬性](../xml-tools/xml-document-properties-properties-window.md)
- [如何：從 XML 文件建立 XML 結構描述](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)