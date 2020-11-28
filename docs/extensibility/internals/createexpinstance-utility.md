---
title: CreateExpInstance 公用程式 |Microsoft Docs
description: 瞭解可讓您建立、重設或刪除實驗 Visual Studio 實例的 CreateExpInstance 公用程式。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c02e85a96d59645787d3018100949369d52c8980
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305375"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance 公用程式
您可以使用 **CreateExpInstance** 公用程式來建立、重設或刪除 Visual Studio 的實驗實例。 您可以使用實驗性實例，在不變更基礎產品的情況下，對 Visual Studio 擴充功能進行調試和測試。

## <a name="syntax"></a>語法

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>參數
 **/Create** 建立實驗實例。

 **/Reset** 刪除實驗實例，然後再建立一個新的實例。

 **/Clean** 刪除實驗實例。

 **/VSInstance** 包含要複製之基底 Visual Studio 實例的目錄名稱。

 **/RootSuffix** 要附加至實驗實例目錄名稱的尾碼。

## <a name="remarks"></a>備註
 當您使用 Visual Studio 擴充功能時，您可以按 F5 來開啟預設的實驗性實例，並安裝目前的擴充功能。 如果沒有可用的實驗實例，Visual Studio 會建立一個具有預設設定的實例。

 實驗實例的預設位置取決於 Visual Studio 版本號碼。 例如，針對 Visual Studio 2015，此位置為 *%localappdata%\Microsoft\VisualStudio\14.0Exp \\*。 目錄位置中的所有檔案都會被視為該實例的一部分。 除非將目錄名稱變更為預設位置，否則 Visual Studio 不會載入任何其他實驗實例。

 Visual Studio 在開啟實驗實例時，不會存取系統登錄。 這與舊版的 Visual Studio 不同，後者使用了實驗版本的登錄 hive。

 **CreateExpInstance** 公用程式會取代 **VsRegEx** 公用程式。

 下列範例會重設 Visual Studio 的預設實驗實例：

 **CreateExpInstance.exe/Reset/VSInstance = 14.0/RootSuffix = Exp**

## <a name="see-also"></a>另請參閱
- [VSPackages](../../extensibility/internals/vspackages.md)
