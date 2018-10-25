---
title: 啟用偵錯 Visual c + + 中的功能 (-D_DEBUG) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e512620e1af8da85039ed403d4280568101fbe57
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829257"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>啟用 Visual C++ 的偵錯功能 (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在  [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]，偵錯功能，例如當您編譯您的程式使用的符號時，會啟用判斷提示 **_DEBUG**定義。 您可以定義 **_DEBUG**中有兩種：  
  
- 指定 **#define _DEBUG**您在原始程式碼中，或  
  
- 指定 **/D_DEBUG**編譯器選項。 (如果您使用精靈，在 Visual Studio 建立您的專案 **/D_DEBUG**偵錯組態中自動定義。)  
  
  當 **_DEBUG**是定義，編譯器會編譯括住的程式碼區段 **#ifdef _DEBUG**和`#endif`。  
  
  MFC 程式的偵錯組態必須與 MFC 程式庫的偵錯版本連結。 MFC 標頭檔判斷正確的版本，若要連結的 MFC 程式庫根據您已定義，這類符號 **_DEBUG**並 **_UNICODE**。 如需詳細資訊，請參閱 < [MFC 程式庫版本](http://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯機器碼](../debugger/debugging-native-code.md)   
 [C++ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)



