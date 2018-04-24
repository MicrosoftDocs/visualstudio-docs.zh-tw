---
title: VSG_NODEFAULT_INSTANCE |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d064f4a5b983058d9f1ad4428e2b37cf2e82dcf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
預設執行個體是否會出現定義[VsgDbg 類別](vsgdbg-class.md)類別，提供程式設計擷取介面 — 提供。  
  
## <a name="syntax"></a>語法  
  
```C++  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>值  
 前置處理器符號會出現，或如果沒有決定的預設執行個體`VsgDbg`類別所提供。 如果已定義這個符號，然後沒有預設的執行個體`VsgDbg`類別所提供，否則預設執行個體是提供您的程式執行之前初始化。  
  
 程式設計擷取介面是具有全域範圍內，透過指標`g_pVsgDbg`。  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>備註  
 預設執行個體通常就已足夠，但若要使用的程式設計擷取介面於 DLL 內外部 DLL 中建立 D3D 裝置後，您必須建立並管理您自己的執行個體`VsgDbg`類別。 如果您要管理您自己的介面，以程式設計擷取 API，以這種方式，來停用的預設執行個體定義`VSG_NODEFAULT_INSTANCE`以避免額外負荷。  
  
 如果預設執行個體未停用，它程式執行之前自動進行初始化，並在程式結束時即會自動終結。 您不必在初始化或明確解除初始化這個執行個體。  
  
 若要停用的預設執行個體，您必須定義`VSG_NODEFAULT_INSTANCE`您包含之前`vsgcapture.h`程式中。  
  
## <a name="example"></a>範例  
 此範例顯示如何停用的預設執行個體：  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```