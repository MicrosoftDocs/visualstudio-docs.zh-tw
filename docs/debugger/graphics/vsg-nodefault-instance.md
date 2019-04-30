---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 304576391b2287aee7567b3ccc2e4514ce5cb2e8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848471"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
預設執行個體是否定義出現[VsgDbg 類別](vsgdbg-class.md)類別，以提供的程式設計擷取介面 — 提供。

## <a name="syntax"></a>語法

```C++
#define VSG_NODEFAULT_INSTANCE
```

## <a name="value"></a>值
 前置處理器符號會出現，或如果沒有決定的預設執行個體`VsgDbg`類別會提供。 如果已定義這個符號，則沒有預設的執行個體`VsgDbg`類別會提供; 否則預設執行個體是提供，並且初始化您的程式執行之前。

 程式設計擷取介面會提供具有全域範圍內，透過指標`g_pVsgDbg`。

```cpp
VsgDbg *g_pVsgDbg;
```

## <a name="remarks"></a>備註
 預設執行個體通常就已足夠，但該 DLL 外部建立 D3D 裝置後，請使用程式設計擷取介面，於 DLL 內，您必須建立並管理您自己的執行個體`VsgDbg`類別。 如果您要管理您自己的介面，以程式設計擷取 API，如此一來，停用的預設執行個體定義`VSG_NODEFAULT_INSTANCE`以避免額外負荷。

 如果預設執行個體未停用，它會自動初始化您的程式執行之前，即會自動終結，當您的程式結束時。 您不必在初始化或明確解除初始化這個執行個體。

 若要停用的預設執行個體，您必須定義`VSG_NODEFAULT_INSTANCE`您加入之前`vsgcapture.h`在程式中。

## <a name="example"></a>範例
 此範例示範如何停用的預設執行個體：

```cpp
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h
#define VSG_NODEFAULT_INSTANCE

#include <vsgcapture.h>
```
