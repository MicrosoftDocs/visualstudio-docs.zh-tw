---
title: 準備進行 Windows 服務的調試 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3161f6d2c328e8e33dd82ed206aa8aa20e654cc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72738080"
---
# <a name="debugging-preparation-windows-services"></a>偵錯準備：Windows 服務
Windows 服務是在 Microsoft Windows 背景中執行的程式。 參考範例包括 Telnet 服務和 Windows 時間服務 (這會更新您電腦上的時鐘)。 Windows 服務不能在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 內執行；它必須在服務控制管理員的內容中執行。 如需詳細資訊，請參閱[建立 Windows 服務](/dotnet/framework/windows-services/how-to-create-windows-services)、[偵錯 Windows 服務應用程式](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)和 [Windows 服務應用程式](/dotnet/framework/windows-services/index)。

## <a name="see-also"></a>另請參閱
- [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
- [C#、F# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C# 偵錯組態的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Project Settings for a Visual Basic Debug Configuration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [How to： Debug OnStart 方法](../debugger/how-to-debug-the-onstart-method.md)