---
title: Visual Basic 特定的 IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9bae55b10695ba73fec86d7ab63943e3440e3f05
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499034"
---
# <a name="visual-basic-specific-intellisense"></a>Visual Basic 特定的 IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[Visual Basic 特定 IntelliSense](https://docs.microsoft.com/visualstudio/ide/visual-basic-specific-intellisense)。  
  
Visual Basic 原始程式碼編輯器提供下列 IntelliSense 功能：  
  
-   語法提示  
  
     語法提示會顯示您正在鍵入的陳述式語法。 這非常適用於陳述式，例如 [Declare](http://msdn.microsoft.com/library/d3f21fb0-b804-4c99-97ed-583b23894cf1)。  
  
## <a name="automatic-completion"></a>自動完成  
  
-   完成各種關鍵字  
  
     例如，如果您鍵入 `goto` 和空格，IntelliSense 會在下拉式功能表中顯示已定義的標籤清單。 其他支援的關鍵字包括 `Exit`、`Implements`、`Option` 和 `Declare`。  
  
-   完成 `Enum` 和 `Boolean`  
  
     當陳述式要參考列舉成員時，IntelliSense 會顯示 `Enum` 的成員清單。 當陳述式要參考 `Boolean` 時，IntelliSense 會顯示 true-false 下拉式功能表。  
  
 完成預設可以關閉，只要在 [Visual Basic] 資料夾取消選取 [一般] 屬性頁的 [自動列出成員] 即可。  
  
 您可以叫用 [列出成員]、[自動完成文字] 或 ALT + 向右鍵，手動叫用完成。 如需詳細資訊，請參閱[使用 IntelliSense](../ide/using-intellisense.md)。  
  
## <a name="intellisense-in-zone"></a>IntelliSense in Zone  
 IntelliSense in Zone 可協助需要透過 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署應用程式，但受限於部分信任設定的 Visual Basic 開發人員。 此功能：  
  
-   可讓您選擇應用程式的執行權限。  
  
-   顯示 [列出成員] 中可用的所選區域 API，以及需要額外權限的無法使用 API。  
  
 如需詳細資訊，請參閱 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 IntelliSense](../ide/using-intellisense.md)



