---
title: MSBuild 特殊字元 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c9ce1697f370ec1beec8ce12faceb15825fbe5f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256447"
---
# <a name="msbuild-special-characters"></a>MSBuild 特殊字元
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 保留一些針對特定內容中特殊用法的字元。 如果您想要在保留這些字元的內容中按字面使用這些字元，只需要將其逸出即可。 比方說，星號僅在項目定義的 `Include` 和 `Exclude` 屬性，以及 `CreateItem` 呼叫中具有特殊意義。 如果您想要將這些內容之一的星號顯示為星號，則必須將其逸出。 而在其他內容中，您只要在想要顯示的位置鍵入星號即可。  
  
 若要逸出特殊字元，請使用 %*xx* 語法，其中 *xx* 代表字元的 ASCII 十六進位值。 如需詳細資訊，請參閱[如何：在 MSBuild 中逸出特殊字元](../msbuild/how-to-escape-special-characters-in-msbuild.md)。  
  
## <a name="special-characters"></a>特殊字元  
 下表列出 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 特殊字元：  
  
|**字元**|**ASCII**|**保留的使用方式**|  
|-------------------|---------------|------------------------|  
|%|%25|參考中繼資料|  
|$|%24|參考屬性|  
|@|%40|參考項目清單|  
|'|%27|條件和其他運算式|  
|;|%3B|清單分隔字元|  
|?|%3F|`Include` 和 `Exclude` 屬性中的檔案名稱萬用字元|  
|*|%2A|用於 `Include` 和 `Exclude` 屬性中的檔案名稱萬用字元|  
  
## <a name="see-also"></a>另請參閱  
 [進階概念](../msbuild/msbuild-advanced-concepts.md)   
 [項目](../msbuild/msbuild-items.md)



