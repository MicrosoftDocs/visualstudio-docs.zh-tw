---
title: 建立PkgDef實用程式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f437eb3586dc16bb0b4b9eb60cd303eb90db6c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709160"
---
# <a name="createpkgdef-utility"></a>建立PkgDef實用程式
將 Visual Studio 副檔名的 .dll 檔作為參數,並創建一個 *.pkgdef*檔來伴隨 *.dll*檔。 *.pkgdef*檔包含安裝副檔名時將寫入系統註冊表的所有資訊。

> [!NOTE]
> Visual Studio SDK 中包含的大多數專案範本都會自動創建 *.pkgdef*檔,作為生成過程的一部分。 本文件適用於希望手動創建包或將現有包轉換為使用 *.pkgdef*部署的使用者。

## <a name="syntax"></a>語法

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>引數
**/out=&lt;檔案名稱&gt;**\
必要。 將 *.pkgdef*輸出檔的名稱&lt;設定到&gt;FileName 。

**/代碼庫**\
選擇性。 強制使用**CodeBase**實用程式進行註冊。

**/裝配**\
強制向**裝配實用程式**註冊。

**&lt;裝配路徑&gt;**\
要從中生成 *.pkgdef*的 *.dll*檔的路徑。

## <a name="remarks"></a>備註
使用 *.pkgdef*檔的擴展部署取代了早期版本的 Visual Studio 的註冊錶要求。

::: moniker range=">=vs-2019"

*.pkgdef*檔案必須安裝在以下位置之一:

- *%本地應用資料%%\微軟_可視化工作室\16.0\擴展\\*

- *%vsinstalldir%\公共7_IDE_擴展\\*

若安裝資料夾是 *%localappdata%\Microsoft_Visual Studio_16.0\\\擴展*,則 Visual Studio 會識別擴展,但默認情況下將禁用該擴展。 使用者可以使用**管理延伸延伸延伸**。

若安裝資料夾為 *%vsvsinstalldir%\Common7_IDE\\\擴展*,則預設情況下將啟用擴展。

> [!NOTE]
> 除非擴展作為 VSIX 套件的一部分安裝,否則「**管理擴展」** 工具不能用於訪問擴展。

::: moniker-end

::: moniker range="vs-2017"

*.pkgdef*檔案必須安裝在以下位置之一:

- *%本地應用資料%%\微軟_可視化工作室\15.0\擴展\\*

- *%vsinstalldir%\公共7_IDE_擴展\\*

若安裝資料夾是 *%localappdata%\Microsoft_Visual Studio_15.0\\\擴展*,則 Visual Studio 會識別擴展,但預設情況下將禁用該擴展。 用戶可以使用**擴展和更新**啟用擴展。

若安裝資料夾為 *%vsvsinstalldir%\Common7_IDE\\\擴展*,則預設情況下將啟用擴展。

> [!NOTE]
> 擴展**和更新**工具不能用於訪問擴展,除非它是作為 VSIX 包的一部分安裝的。

::: moniker-end

## <a name="see-also"></a>另請參閱
- [建立 ExpInstance 實用程式](../../extensibility/internals/createexpinstance-utility.md)
