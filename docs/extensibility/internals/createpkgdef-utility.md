---
title: CreatePkgDef 公用程式 |Microsoft Docs
description: 瞭解 CreatePkgDef 公用程式，此公用程式會將 Visual Studio 擴充功能的 .dll 檔案作為參數，並建立與 .dll 檔案伴隨的 .pkgdef 檔案。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: aa0b0e3e8ea59ce1d41f9d8a6c056239f2bc0e9a
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305550"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef 公用程式
取得 Visual Studio 擴充功能的 .dll 檔作為參數，並建立與 *.dll* 檔案伴隨的 *.pkgdef* 檔案。 *.Pkgdef* 檔案包含在安裝擴充功能時，將寫入系統登錄的所有資訊。

> [!NOTE]
> Visual Studio SDK 中包含的大部分專案範本會在組建程式中自動建立 *.pkgdef 檔案。* 本檔適用于想要手動建立套件，或轉換現有套件以使用 *.pkgdef*  部署的使用者。

## <a name="syntax"></a>語法

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>引數
**/out = &lt; FileName&gt;**\
必要。 將 *.pkgdef* 輸出檔的名稱設定為 &lt; FileName &gt; 。

**/codebase**\
選擇性。 強制註冊程式 **代碼基** 底公用程式。

**/assembly**\
強制註冊 **元件** 公用程式。

**&lt;AssemblyPath&gt;**\
您要從中產生 *.pkgdef* 之 *.dll* 檔案的路徑。

## <a name="remarks"></a>備註
使用 *.pkgdef* 檔案進行擴充部署，會取代舊版 Visual Studio 的登錄需求。

::: moniker range=">=vs-2019"

*.Pkgdef* 檔案必須安裝在下列其中一個位置：

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

如果安裝資料夾是 *%Localappdata%\Microsoft\Visual Studio\16.0\Extensions \\*，則會 Visual Studio 辨識擴充功能，但預設為停用。 使用者可以使用 [ **管理延伸** 模組] 來啟用擴充功能。

如果安裝資料夾是 *%vsinstalldir%\Common7\IDE\Extensions \\*，則預設會啟用擴充功能。

> [!NOTE]
> 除非將擴充功能安裝為 VSIX 套件的一部分，否則無法使用 [ **管理擴充** 功能] 工具來存取擴充功能。

::: moniker-end

::: moniker range="vs-2017"

*.Pkgdef* 檔案必須安裝在下列其中一個位置：

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

如果安裝資料夾是 *%Localappdata%\Microsoft\Visual Studio\15.0\Extensions \\*，則會 Visual Studio 辨識擴充功能，但預設為停用。 使用者可以使用 **擴充功能和更新** 來啟用擴充功能。

如果安裝資料夾是 *%vsinstalldir%\Common7\IDE\Extensions \\*，則預設會啟用擴充功能。

> [!NOTE]
> [ **擴充功能和更新** ] 工具無法用來存取擴充功能，除非它安裝為 VSIX 封裝的一部分。

::: moniker-end

## <a name="see-also"></a>另請參閱
- [CreateExpInstance 公用程式](../../extensibility/internals/createexpinstance-utility.md)
