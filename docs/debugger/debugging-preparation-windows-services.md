---
title: 準備進行 Windows 服務的調試 |Microsoft Docs
description: 準備在 Visual Studio 中，偵錯工具是在 Windows 下的背景中執行的程式。
ms.custom: SEO-VS-2020, seodec18
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdf82b708440cb3201c5d05bd936c7f7d9c30729
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872387"
---
# <a name="debugging-preparation-windows-services"></a>偵錯準備：Windows 服務
Windows 服務是在 Microsoft Windows 背景中執行的程式。 參考範例包括 Telnet 服務和 Windows 時間服務 (這會更新您電腦上的時鐘)。 Windows 服務不能在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 內執行；它必須在服務控制管理員的內容中執行。 如需詳細資訊，請參閱[建立 Windows 服務](/dotnet/framework/windows-services/how-to-create-windows-services)、[偵錯 Windows 服務應用程式](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)和 [Windows 服務應用程式](/dotnet/framework/windows-services/index)。

## <a name="see-also"></a>另請參閱
- [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
- [C#、F# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C # Debug 設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic Debug 設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [How to： Debug OnStart 方法](../debugger/how-to-debug-the-onstart-method.md)