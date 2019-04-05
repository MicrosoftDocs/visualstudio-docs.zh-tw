---
title: 啟用偵錯 Visual c + + 中的功能 (-D_DEBUG) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4cbaa01cfde69db639f354f3d68bd6bbee82efc9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940888"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>啟用 Visual C++ 的偵錯功能 (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 中，當您使用已定義的 **_DEBUG** 符號編譯您的程式時，便會啟用判斷提示之類的偵錯功能。 您可以使用下列兩種方法之一定義 **_DEBUG**：  
  
- 在原始程式碼中指定 **#define _DEBUG**，或  
  
- 指定 **/D_DEBUG** 編譯器選項。 (如果您在 Visual Studio 中使用精靈建立專案，會在偵錯組態中自動定義 **/D_DEBUG**。)  
  
  當 **_DEBUG** 定義好之後，編譯器便會編譯 **#ifdef _DEBUG** 和 `#endif` 所包圍的程式碼區段。  
  
  MFC 程式的偵錯組態必須與 MFC 程式庫的偵錯版本連結。 MFC 標頭檔會根據您已定義的符號，例如 **_DEBUG** 和 **_UNICODE**，來決定要連結到哪一個正確版本的 MFC 程式庫。 如需詳細資訊，請參閱 [MFC 程式庫版本](http://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯機器碼](../debugger/debugging-native-code.md)   
 [C++ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)
