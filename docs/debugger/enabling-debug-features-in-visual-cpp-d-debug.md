---
title: 在 c + + 專案中啟用 Debug 功能 (-D_DEBUG) |Microsoft Docs
description: 在 Visual C++ 您可以藉由定義 _DEBUG 來啟用偵錯工具功能。 瞭解如何進行這項作業，並瞭解如何連結 MFC 程式以進行調試。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 1a2ead92108d66b54342019fc19702e7a6e53575
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862929"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>在 c + + 專案中啟用 Debug 功能 (/D_DEBUG) 
在 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 中，當您使用已定義的 **_DEBUG** 符號編譯您的程式時，便會啟用判斷提示之類的偵錯功能。 您可以使用下列兩種方法之一定義 **_DEBUG**：

- 在原始程式碼中指定 **#define _DEBUG**，或

- 指定 **/D_DEBUG** 編譯器選項。 (如果您在 Visual Studio 中使用精靈建立專案，會在偵錯組態中自動定義 **/D_DEBUG**。)

  當 **_DEBUG** 定義好之後，編譯器便會編譯 **#ifdef _DEBUG** 和 `#endif` 所包圍的程式碼區段。

  MFC 程式的偵錯組態必須與 MFC 程式庫的偵錯版本連結。 MFC 標頭檔會根據您已定義的符號，例如 **_DEBUG** 和 **_UNICODE**，來決定要連結到哪一個正確版本的 MFC 程式庫。 如需詳細資訊，請參閱 [MFC 程式庫版本](/cpp/mfc/mfc-library-versions)。

## <a name="see-also"></a>另請參閱
- [偵錯機器碼](../debugger/debugging-native-code.md)
- [C + + 偵錯工具設定的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)