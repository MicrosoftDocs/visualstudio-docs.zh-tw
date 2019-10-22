---
title: HOW TO：編輯 XML 檔案
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd8671bf45230ec24a37d5006a2d32e5aabe8f28
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645929"
---
# <a name="how-to-edit-xml-files"></a>如何：編輯 XML 檔案

XML 編輯器是 XML 檔案的新編輯器。 它可用於獨立 XML 檔案或與 Visual Studio 專案相關的檔案上。 XML 編輯器與下列副檔名相關聯： *.config*、 *. dtd*、 *.xml*、 *.xsd*、 *xdr*、 *.xsl*、 *xslt*和 *.vssettings*。 XML 編輯器也會與任何其他沒有註冊特定編輯器的檔案類型相關聯，並包含 XML 或 DTD 內容。

> [!NOTE]
> HTML 編輯器可處理 XHTML 文件。

若要編輯 XML 檔案，請按兩下您想要編輯的檔案。

## <a name="add-a-new-xml-file-to-a-project"></a>將新的 XML 檔案加入至專案

1. 從 [**專案**] 功能表中，選取 [**加入新專案**]。

2. 從 [**範本**] 窗格中選取 [ **XML**檔案]。

3. 在 [**名稱**] 欄位中輸入檔案名，然後按 [**新增**]。

   XML 檔案會加入至專案，並在 XML 編輯器中開啟。 檔案包含預設的 XML 宣告，`<?xml version="1.0" encoding="utf-8" ?>`。

## <a name="add-an-existing-xml-file-to-a-project"></a>將現有的 XML 檔案加入至專案

1. 從 [**專案**] 功能表中，選取 [**加入現有專案**]。

   [**加入現有專案**] 對話方塊隨即出現。

2. 選取 XML 檔案，然後按 [**新增**]。

## <a name="create-a-new-xml-or-xslt-file"></a>建立新的 XML 或 XSLT 檔案

1. 從 [**檔案**] 功能表中，選取 [**新增**]。

   [**新增**檔案] 對話方塊隨即出現。

2. 選取 [ **xml**檔案] 以建立新的 xml 檔案;或者，選取 [ **xslt**檔案] 以建立新的 xslt 樣式表單。

3. 按一下 [開啟]。

## <a name="create-an-empty-project-for-xml-files"></a>建立 XML 檔案的空白專案

::: moniker range="vs-2017"

1. 從 [檔案] 功能表選取 [新增] > [專案]。

   [ **新增專案** ] 對話方塊隨即出現。

2. 選取您選擇的程式碼語言，然後選取 [**空白專案（.NET Framework）** ] 範本。

3. 按一下 [確定]。

::: moniker-end

::: moniker range=">=vs-2019"

1. 從 [檔案] 功能表選取 [新增] > [專案]。

2. 在 [範本搜尋] 方塊中輸入**空的專案**，選取 [**空白專案（.NET Framework）** ] 範本，然後按 **[下一步]** 。

3. 按一下 [建立]。

::: moniker-end

4. 將 XML 檔案加入至專案。

   XML 編輯器會尋找您加入此專案的架構，並在您于開啟此專案時編輯的任何 XML、架構或 XSLT 檔案中，使用它們來進行驗證和 IntelliSense。

## <a name="see-also"></a>請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)
- [屬性視窗、XML 文件屬性](../xml-tools/xml-document-properties-properties-window.md)
- [如何：從 XML 檔建立 XML 架構](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)