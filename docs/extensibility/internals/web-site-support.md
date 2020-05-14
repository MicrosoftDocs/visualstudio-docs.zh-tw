---
title: 網站支援 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22047ad1b0709cefa200656e61f8e0d39ace94c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703449"
---
# <a name="web-site-support"></a>網站支援
網站專案系統是創建 Web 專案的專案系統。 Web 專案反過來創建 Web 應用程式。 網站專案為具有關聯代碼的每個網頁生成一個可執行檔。 其他可執行檔從 /App_Code 資料夾中的原始程式碼檔生成。

 網站專案系統是通過向現有專案系統添加範本和註冊屬性來創建的。 這些屬性之一為語言選擇 IntelliSense 提供程式。 當請求未快取的智慧 Web 頁時,IntelliSense 提供程式實現處理引用並調用語言編譯器。

 編譯網頁的語言編譯器必須註冊到[!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]。 您可以在 Web.config 檔中使用[\<編譯器>元素](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element)來註冊編譯器,如以下範例所示:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>本節內容
- [網站支援範本](../../extensibility/internals/web-site-support-templates.md)

 列出可用於創建新網站項目和相關項的範本。

- [網站支援屬性](../../extensibility/internals/web-site-support-attributes.md)

 顯示將網站專案連接到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和[!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]的註冊屬性。

## <a name="related-sections"></a>相關章節
- [Web 專案](../../extensibility/internals/web-projects.md)

 概述了兩種類型的 Web 專案,即網站專案和 Web 應用程式專案。
