---
title: HOW TO：編輯 XML 檔案
ms.date: 11/04/2016
description: 瞭解如何使用 Visual Studio 中的 XML 編輯器來編輯包含 XML 或 DTD 內容的檔案。
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c538e9a4da3c4bbd08c571818dbaaaca466c2471
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948540"
---
# <a name="how-to-edit-xml-files"></a>How to：編輯 XML 檔案

XML 編輯器是 XML 檔案的新編輯器。 它可用於獨立 XML 檔案或與 Visual Studio 專案相關的檔案上。 XML 編輯器與下列副檔名相關聯： *.config*、 *.xsd、* *.xml*、 *.xsd*、 *xdr*、 *.xsl*、 *xslt* 和 *. .vssettings*。 XML 編輯器也會與未註冊特定編輯器的任何其他檔案類型相關聯，而且包含 XML 或 DTD 內容。

> [!NOTE]
> HTML 編輯器可處理 XHTML 文件。

若要編輯 XML 檔案，請開啟您要編輯的檔案。

## <a name="add-a-new-xml-file-to-a-project"></a>將新的 XML 檔案加入至專案

1. 從 [ **專案** ] 功能表選取 [ **加入新專案**]。

2. 從 [**範本**] 窗格中選取 [ **XML** 檔案]。

3. 在 [ **名稱** ] 欄位中輸入檔案名，然後按 [ **新增**]。

   XML 檔案隨即加入至專案，並在 XML 編輯器中開啟。 檔案包含預設的 XML 宣告，`<?xml version="1.0" encoding="utf-8" ?>`。

## <a name="add-an-existing-xml-file-to-a-project"></a>將現有的 XML 檔案加入至專案

1. 從 [專案] 功能表上，選取 [新增現有項目]。

   [ **加入現有專案** ] 對話方塊隨即出現。

2. 選取 XML 檔案，然後按 [ **新增**]。

## <a name="create-a-new-xml-or-xslt-file"></a>建立新的 XML 或 XSLT 檔案

1. 從 [ **檔案** ] 功能表選取 [ **新增**]。

   [ **新增檔案** ] 對話方塊隨即出現。

2. 選取 **xml** 檔案以建立新的 xml 檔案;或者，選取 [ **xslt** 檔] 以建立新的 xslt 樣式表單。

3. 選取 [開啟]  。

## <a name="create-an-empty-project-for-xml-files"></a>為 XML 檔案建立空白專案

::: moniker range="vs-2017"

1. 從 [ **檔案** ] 功能表選取 [ **新增** > **專案**]。

   [新增專案]  對話方塊隨即出現。

2. 選取您選擇的程式碼語言，然後選取 [ **空專案] ( .NET Framework)** 範本。

3. 選取 [確定]。

::: moniker-end

::: moniker range=">=vs-2019"

1. 從 [ **檔案** ] 功能表選取 [ **新增** > **專案**]。

2. 在 [範本搜尋] 方塊中輸入 **空白專案** ， **( .NET Framework)** 範本中選取 [空白專案]，然後選取 **[下一步]**。

3. 選取 [建立]  。

::: moniker-end

4. 將 XML 檔案加入至專案。

   XML 編輯器會尋找您加入此專案的架構，並在您于此專案開啟時編輯的任何 XML、架構或 XSLT 檔案中，使用這些架構來進行驗證和 IntelliSense。

## <a name="see-also"></a>另請參閱

- [XML 編輯器](../xml-tools/xml-editor.md)
- [XML 文件屬性，屬性視窗](../xml-tools/xml-document-properties-properties-window.md)
- [如何：從 XML 檔建立 XML 架構](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
