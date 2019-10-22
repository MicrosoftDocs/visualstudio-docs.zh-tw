---
title: 如何：編輯 XML 檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c099839cda87819ec0ec7932c2b2e6aa7698fa52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670876"
---
# <a name="how-to-edit-xml-files"></a>HOW TO：編輯 XML 檔案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 編輯器是 XML 檔案的新編輯器。 它可用於獨立 XML 檔案或與 Visual Studio 專案相關的檔案上。 XML 編輯器與下列副檔名相關：.config、.dtd、.xml、.xsd、.xdr、.xsl、.xslt 和 .vssettings。 XML 編輯器也與未登錄特定編輯器，且包含 XML 或 DTD 內容的任何其他檔案類型相關聯。

> [!NOTE]
> HTML 編輯器可處理 XHTML 文件。

### <a name="to-edit-an-xml-file"></a>編輯 XML 檔案

1. 按兩下要編輯的檔案。

### <a name="to-add-a-new-xml-file-to-a-project"></a>將新的 XML 檔案加入至專案

1. 從 [**專案**] 功能表中，選取 [**加入新專案**]。

2. 從 [**範本**] 窗格中選取 [ **XML**檔案]。

3. 在 [**名稱**] 欄位中輸入檔案名，然後按 [**新增**]。

     將 XML 檔案加入至專案，並在 XML 編輯器中開啟它。 檔案包含預設的 XML 宣告，`<?xml version="1.0" encoding="utf-8" ?>`。

### <a name="to-add-an-existing-xml-file-to-a-project"></a>將現有 XML 檔案加入至專案

1. 從 [**專案**] 功能表中，選取 [**加入現有專案**]。

     [**加入現有專案**] 對話方塊隨即出現。

2. 選取 XML 檔案，然後按 [**新增**]。

### <a name="to-create-a-new-xml-or-xslt-file"></a>建立新的 XML 或 XSLT 檔

1. 從 [**檔案**] 功能表中，選取 [**新增**]。

     [**新增**檔案] 對話方塊隨即出現。

2. 選取 [ **xml**檔案] 以建立新的 xml 檔案;或者，選取 [ **xslt**檔案] 以建立新的 xslt 樣式表單。

3. 按一下 [開啟]。

### <a name="to-create-a-project-for-xml-files"></a>建立 XML 檔案的專案

1. 從 [**檔案**] 功能表中，選取 [**新增**]，然後選取 [**專案**]。

     [ **新增專案** ] 對話方塊隨即出現。

2. 選取您選擇的程式碼語言，選取 [**空白專案**]，然後按一下 **[確定]** 。

3. 將 XML 檔案加入至專案。

     XML 編輯器會找到加入至此專案的結構描述，並在此專案開啟時編輯的任何 XML、結構描述或 XSLT 檔案中使用它們進行驗證及 IntelliSense。

## <a name="see-also"></a>請參閱
 [Xml 編輯器](../xml-tools/xml-editor.md) [xml 文件屬性，屬性視窗](../xml-tools/xml-document-properties-properties-window.md)[如何：從 xml 檔建立 xml 架構](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
