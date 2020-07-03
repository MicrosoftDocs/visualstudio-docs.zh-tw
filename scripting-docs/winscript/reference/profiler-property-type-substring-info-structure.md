---
title: PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 結構 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3845c872-4302-47b6-8912-7b2d7a3b3357
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 3dd3f1e95436805ccc6e07ca45b5864666e52188
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835390"
---
# <a name="profiler_property_type_substring_info-structure"></a>PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 結構
表示關聯性中所使用之子字串類型的相關資訊。 用於[PROFILER_HEAP_OBJECT_RELATIONSHIP 結構](../../winscript/reference/profiler-heap-object-relationship-structure.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct _PROFILER_PROPERTY_TYPE_SUBSTRING_INFO {    UINT length;    LPCWSTR value; } PROFILER_PROPERTY_TYPE_SUBSTRING_INFO;  
```  
  
## <a name="members"></a>成員  
  
|member|類型|說明|  
|------------|----------|-----------------|  
|長度|UINT|物件是 UINT。|  
|value|LPCWSTR|此物件為 LPCWSTR。|