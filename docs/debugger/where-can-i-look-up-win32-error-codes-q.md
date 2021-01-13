---
title: 哪裡可以查看 Win32 錯誤碼？ | Microsoft Docs
description: 若要查閱 Win32 錯誤碼，請在 [監看式] 或 [快速監看式] 中輸入。 例如「0x80000004，hr」。 錯誤碼定義位於 INCLUDE\WINERROR.H。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44a006be3b6ecad3ef723c00154354cb35df0049
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149283"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>哪裡可以查看 Win32 錯誤碼？
您的預設系統安裝 INCLUDE 目錄裡的 WINERROR.H 包含 Win32 API 函式的錯誤碼定義。

 您可以在 [監看式] 視窗或 [快速監看式] 對話方塊中鍵入程式碼來查看錯誤碼。 例如：

`0x80000004,hr`

## <a name="see-also"></a>另請參閱
- [原生程式碼的偵錯工具常見問題](../debugger/debugging-native-code-faqs.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)