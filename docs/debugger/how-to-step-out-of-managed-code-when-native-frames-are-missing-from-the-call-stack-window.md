---
title: 如何： 原生框架遺失於呼叫堆疊視窗時跳離 Managed 程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e5c671f93e20da108a9fd1069a0950f52ef00da9
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388565"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>如何：在原生框架遺失於呼叫堆疊顯示時跳離 Managed 程式碼

如果程式碼擁有在 [呼叫堆疊 **] 視窗中不可見的原生框架，跳離 Managed 程式碼函式則可以產生未預期的結果。 您可使用中斷點，而不要使用跳離函式 **，便可解決這個問題。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 <<c0> [ 重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>若要在原生框架遺失於呼叫堆疊顯示時跳離 Managed 程式碼

1.  在機器碼中，請在呼叫 Managed 程式碼之後設定一個位置中斷點。

2.  選擇 [偵錯 **] 功能表上的 [繼續**]。

     完成 Managed 呼叫之後，執行將停止於機器碼的中斷點處。

## <a name="see-also"></a>另請參閱

- [如何：使用呼叫堆疊視窗](../debugger/how-to-use-the-call-stack-window.md)