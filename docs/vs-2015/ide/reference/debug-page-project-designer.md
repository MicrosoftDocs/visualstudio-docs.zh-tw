---
title: 專案設計工具、偵錯頁面 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 006662d7c07ba0498fff4617eca3fdc7c631d37b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660791"
---
# <a name="debug-page-project-designer"></a>專案設計工具、偵錯頁
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!WARNING]
> 本主題不適用於 Windows 市集應用程式。 請參閱 Windows 開發人員中心的[開始偵錯工作階段 (VB、C#、C++ 和 XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)。

 使用專案設計工具**** 的 [偵錯頁面]**** 設定在 Visual Basic 或 C# 專案中的偵錯行為屬性。

 若要存取 [偵錯]**** 頁面，請選取方案總管**** 中的專案節點。 在 [ **專案** ] 功能表上，選擇 [專案 _名稱_**屬性**]。 當專案設計工具**** 出現時，請按一下 [偵錯]**** 索引標籤。

## <a name="configuration-and-platform"></a>組態和平台
 下列選項可讓您選取要顯示或修改的設定和平台。

 **組態** 指定要顯示或修改的組態設定。 設定可以是 [偵錯]**** (預設)、[發行]**** 或 [所有設定]****。 如需詳細資訊，請參閱[偵錯和發行專案組態](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)。

 **平台** 指定要顯示或修改的平台設定。 選項可以包括 [任何 CPU]**** (預設)、[x64]**** 和 [x86]****。 如需詳細資訊，請參閱[偵錯和發行專案組態](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)。

## <a name="start-action"></a>啟動執行
 **開始動作** 表示在應用程式進行調試時要啟動的專案：專案、自訂程式、URL 或 nothing。 根據預設，這個選項會設為 [起始專案]****。 [偵錯]**** 頁面上的 [起始動作]**** 設定會決定 `StartAction` 屬性的值。

 **開始專案** 選擇這個選項可指定在應用程式進行調試時，應啟動 Windows 應用程式和主控台應用程式專案) 的可執行檔 (。 預設會選取這個選項。

 **啟動外部程式** 選擇這個選項可指定在應用程式進行調試時應啟動特定程式。

 **以 URL 啟動瀏覽器** 選擇這個選項可指定在應用程式進行調試時應存取特定的 URL。

## <a name="start-options"></a>起始選項
 **命令列引數** 在這個文字方塊中，輸入要用於偵錯工具的命令列引數。

 **工作目錄** 在這個文字方塊中，輸入將啟動專案的目錄。 或按一下 [瀏覽] 按鈕 (**...**) 選擇目錄。

 **使用遠端電腦** 若要從遠端電腦進行應用程式的偵錯工具，請選取此核取方塊，然後在文字方塊中輸入遠端電腦的路徑。

## <a name="enable-debuggers"></a>啟用偵錯工具
 **啟用非受控程式碼調試** 程式此選項會指定是否支援原生程式碼的偵錯工具。 如果您正在呼叫 COM 物件，或如果您啟動以原生程式碼撰寫的自訂程式，而它會呼叫您的專案且您必須對原生程式碼進行偵錯，請選取此核取方塊。 清除此核取方塊可停用非受控碼的偵錯。 依預設，不會勾選此核取方塊。

 **啟用 SQL Server 的調試** 選取或清除此核取方塊，即可從您的 Visual Basic 應用程式啟用或停用 SQL 程式的偵錯工具。 依預設，不會勾選此核取方塊。

 **啟用 Visual Studio 裝載進程** 選取此核取方塊以啟用 Visual Studio 裝載進程。 依預設，這個核取方塊為已選取。 如需詳細資訊，請參閱[裝載處理序 (vshost.exe)](../../ide/hosting-process-vshost-exe.md)。

 若要在安全性區域中進行偵錯，您必須在 [進階安全性設定]**** 對話方塊中，啟用這個選項和[以選取的使用權限集合對此應用程式進行偵錯](../../ide/reference/advanced-security-settings-dialog-box.md)。

## <a name="see-also"></a>另請參閱
 [在](../../debugger/debugging-in-visual-studio.md) [c # 調試](../../debugger/project-settings-for-csharp-debug-configurations.md)程式的 Visual Studio 專案設定中進行偵錯工具的[Visual Basic Debug 設定的設定專案設定](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)[管理偵錯工具屬性](https://msdn.microsoft.com/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)[如何：以限制許可權對 ClickOnce 應用程式進行偵錯工具](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)[如何：建立和編輯](../../ide/how-to-create-and-edit-configurations.md)設定
