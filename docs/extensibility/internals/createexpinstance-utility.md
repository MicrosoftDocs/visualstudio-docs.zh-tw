---
title: 建立實體實用程式 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a6b302976495e6067fad14317856cda4ac4625f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709247"
---
# <a name="createexpinstance-utility"></a>建立 ExpInstance 實用程式
使用**CreateExpInstance**實用程式創建、重置或刪除 Visual Studio 的實驗實例。 您可以使用實驗實例調試和測試 Visual Studio 擴展,而無需更改基礎產品。

## <a name="syntax"></a>語法

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>參數
 **/建立**創建實驗實例。

 **/重置**刪除實驗實例,然後創建新實例。

 **/清潔**刪除實驗實例。

 **/VS實體**包含要複製的基本 Visual Studio 實體的目錄名稱。

 **/根素綴**追加到實驗實例目錄名稱的後綴。

## <a name="remarks"></a>備註
 處理 Visual Studio 擴充時,可以按 F5 打開預設實驗實例並安裝當前擴展。 如果沒有可用的實驗實例,Visual Studio 將創建具有預設設置的實例。

 實驗實例的預設位置取決於 Visual Studio 版本號。 例如,對於 Visual Studio 2015,位置為 *%localappdata%*微軟_VisualStudio_14.0Exp\\*。 目錄位置中的所有檔都被視為該實例的一部分。 除非目錄名稱更改為預設位置,否則 Visual Studio 不會載入任何其他實驗實例。

 Visual Studio 打開實驗實例時無法訪問系統註冊表。 這與早期版本的 Visual Studio 不同,後者使用註冊表配置單元的實驗版本。

 **CreateExpEx**實用程式取代了**VsRegEx**實用程式。

 以下範例重置 Visual Studio 的預設實驗實例:

 **建立Expinstance.exe /重置/VSInstance=14.0 /RootSuffix_Exp**

## <a name="see-also"></a>另請參閱
- [VSPackage](../../extensibility/internals/vspackages.md)
