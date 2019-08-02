---
title: 專案設計工具、偵錯頁
ms.date: 06/27/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1f54485a4dd47b0aec4401f6cdfb39072e9f8cf
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461400"
---
# <a name="debug-page-project-designer"></a>專案設計工具、偵錯頁

使用專案設計工具  的 [偵錯頁面]  設定在 Visual Basic 或 C# 專案中的偵錯行為屬性。

若要存取 [偵錯]  頁面，請選取方案總管  中的專案節點。 在 [專案]  功能表上，選擇 [\<專案名稱> 屬性]  。 當專案設計工具  出現時，請按一下 [偵錯]  索引標籤。

> [!NOTE]
> 本主題不適用於 UWP 應用程式。 若為 UWP 應用程式，請參閱[啟動偵錯工作階段 (VB、C#、C++ 和 XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)。

## <a name="configuration-and-platform"></a>組態和平台

下列選項可讓您選取要顯示或修改的設定和平台。

**組態**

指定要顯示或修改的組態設定。 設定可以是 [偵錯]  (預設)、[發行]  或 [所有設定]  。

**平台**

指定要顯示或修改的平台設定。 選項可以包括 [任何 CPU]  (預設)、[x64]  和 [x86]  。

## <a name="start-action"></a>起始動作

**起始動作**指出在對應用程式進行偵錯時要啟動的項目：專案、自訂程式、URL 或不啟動任何項目。 根據預設，這個選項會設為 [起始專案]  。 [偵錯]  頁面上的 [起始動作]  設定會決定 `StartAction` 屬性的值。

**起始專案**

選擇這個選項可指定在對應用程式進行偵錯時，應該要啟動可執行檔 (適用於 Windows 應用程式和主控台應用程式專案)。 預設會選取這個選項。

**起始外部程式**

選擇這個選項可指定在對應用程式進行偵錯時，應該要啟動特定程式。

**以 URL 啟動瀏覽器**

選擇這個選項可指定在對應用程式進行偵錯時，應該要存取特定 URL。

## <a name="start-options"></a>起始選項

**命令列引數**

在這個文字方塊中，輸入要用於偵錯的命令列引數。

**工作目錄**

在這個文字方塊中，輸入將從中啟動專案的目錄。 或按一下 [瀏覽] 按鈕 ( **...** ) 選擇目錄。

**使用遠端電腦**

若要從遠端電腦對應用程式進行偵錯，請選取此核取方塊，然後在文字方塊中輸入遠端電腦的路徑。

## <a name="debugger-engines"></a>偵錯工具引擎

**啟用機器碼偵錯**

這個選項會指定是否支援原生程式碼的偵錯。 如果您正在呼叫 COM 物件，或如果您啟動以原生程式碼撰寫的自訂程式，而它會呼叫您的專案且您必須對原生程式碼進行偵錯，請選取此核取方塊。 清除此核取方塊可停用非受控碼的偵錯。 此核取方塊預設為清除。

**啟用 SQL Server 偵錯**

選取或清除此核取方塊，可啟用或停用從 Visual Basic 應用程式進行 SQL 程序的偵錯。 此核取方塊預設為清除。

## <a name="see-also"></a>另請參閱

- [偵錯工具簡介](../../debugger/debugger-feature-tour.md)
- [C# 偵錯組態的專案設定](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 偵錯組態的專案設定](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [如何：以受限制的權限針對 ClickOnce 應用程式進行偵錯](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [如何：建立及編輯組態](../../ide/how-to-create-and-edit-configurations.md)