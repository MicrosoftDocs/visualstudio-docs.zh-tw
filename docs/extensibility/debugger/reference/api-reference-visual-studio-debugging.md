---
title: API 參考(可視化工作室調試) |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a2df6d82099a927664620e19096107f283afada
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738184"
---
# <a name="api-reference-visual-studio-debugging"></a>API 參考 (Visual Studio 偵錯)
參考部分包括 API 的概念概述、顯示所有 API 元素的語法和用法的指南以及各種代碼示例。 所有引用按類別按字母順序出。

 下表顯示了方法返回的通用`HRESULT`值。

|名稱|描述|值|
|----------|-----------------|-----------|
|S_OK|成功。|0x00000000|
|E_UNEXPECTED|發生非預期的失敗。|0x8000FFFF|
|E_NOTIMPL|未實作。|0x80004001|
|E_OUTOFMEMORY|記憶體不足以完成操作。|0x8007000E|
|E_INVALIDARG|一個或多個參數無效。|0x80070057|
|E_NOINTERFACE|不支援此類介面。|0x80004002|
|E_POINTER|無效指標。|0x80004003|
|E_HANDLE|句柄無效。|0x80070006|
|E_ABORT|作業已中止。|0x80004004|
|E_FAIL|發生非預期的失敗。|0x80004005|
|E_ACCESSDENIED|常規訪問被拒絕錯誤。|0x80070005|

> [!NOTE]
> 當[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]調試方法`S_OK`返回 時,假定所有出參數指標都有效,也就是說,返回時不會對 out`S_OK`參數指標執行驗證。
>
> [!NOTE]
> 無效或`NULL`[out] 參數可能導致 IDE 崩潰。

## <a name="see-also"></a>另請參閱
- [介面](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [適用於偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Visual Studio 偵錯工具的擴充性](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
