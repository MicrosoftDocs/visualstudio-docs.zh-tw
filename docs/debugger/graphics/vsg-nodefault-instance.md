---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ed60fb5262a6af07966ff974b8535ae299f3fc51
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861409"
---
# <a name="vsg_nodefault_instance"></a>VSG_NODEFAULT_INSTANCE
定義是否提供 [VsgDbg 類別](vsgdbg-class.md) 類別的預設實例（可提供程式設計的捕獲介面），藉此定義它的存在。

## <a name="syntax"></a>Syntax

```C++
#define VSG_NODEFAULT_INSTANCE
```

## <a name="value"></a>值
 預處理器符號，其存在或不存在會決定是否提供類別的預設實例 `VsgDbg` 。 如果已定義此符號，則不 `VsgDbg` 會提供類別的預設實例; 否則，會在您的程式執行之前提供並初始化預設實例。

 程式設計捕獲介面是透過具有全域範圍的指標來提供 `g_pVsgDbg` 。

```cpp
VsgDbg *g_pVsgDbg;
```

## <a name="remarks"></a>備註
 預設實例通常已足夠，但若要在該 DLL 外部建立 D3D 裝置時，在 DLL 內使用程式設計捕獲介面，您必須建立並管理您自己的 `VsgDbg` 類別實例。 如果您以這種方式管理自己的介面至程式設計捕獲 API，請定義以停用預設實例， `VSG_NODEFAULT_INSTANCE` 以避免額外負荷。

 如果預設實例未停用，它會在您的程式執行之前自動初始化，並在程式結束時自動損毀。 您不需要明確地將此實例初始化或解除初始化。

 若要停用預設實例，您必須 `VSG_NODEFAULT_INSTANCE` 先定義，然後再包含 `vsgcapture.h` 在程式中。

## <a name="example"></a>範例
 此範例說明如何停用預設實例：

```cpp
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h
#define VSG_NODEFAULT_INSTANCE

#include <vsgcapture.h>
```
