---
title: JavaScript、屬性頁 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1fe8acd8628fcbd40e9c675558379049fd6658b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665737"
---
# <a name="property-pages-javascript"></a>JavaScript、屬性頁
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[屬性頁] 可讓您存取專案設定。 您可以使用 [屬性頁] 中所顯示的頁面來變更專案屬性。

 若要存取專案屬性，請選取方案總管中的專案節點。 在 [專案] 功能表上，按一下 [屬性]。

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 [屬性頁] 中隨即出現下列頁面和選項。

## <a name="configuration-and-platform-page"></a>組態和平台頁面
 您可以使用下列選項，來選取要顯示或修改的組態和平台。

 設定指定要顯示或修改的設定。 這些設定包括 [偵錯]\(預設值)、[發行]、[所有組態] 或使用者定義的組態。 如需詳細資訊，請參閱[偵錯和發行專案組態](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)。

 **平臺**指定要顯示或修改的平臺設定。 這些設定包括 [任何 CPU]\([!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] 應用程式的預設值)、[x64]、[ARM]、[x86] 或使用者定義的平台。 如需詳細資訊，請參閱[偵錯和發行專案組態](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)。

## <a name="general-page"></a>一般頁面
 您可以使用下列選項，來設定專案的一般屬性。

> [!NOTE]
> 有些選項僅適用於 Windows 市集應用程式。

 **輸出路徑**指定專案設定的輸出檔位置。 路徑是相對的；如果您輸入絕對路徑，則會在專案中儲存絕對路徑。 預設路徑為 bin\Debug。

 當您使用簡化的組建組態時，專案系統會決定要建置偵錯或發行版本。 不論您指定的 [輸出路徑] 為何，按一下 [偵錯]、[開始偵錯] (或按 F5) 時，組建均會放在偵錯位置。 但是，[建置] 功能表上的 [建置方案] 命令卻會將其放在您指定的位置。 若要啟用進階組建組態，請在功能表列上選擇 [工具]、[選項]。 在 [選項] 對話方塊中，展開 [專案和方案]，選取 [一般]，然後清除 [顯示進階組建組態] 核取方塊。 這麼做可以讓您手動控制所有組態值，以及建置的是偵錯或發行版本。 如需詳細資訊，請參閱[[選項] 對話方塊、[筆尖：一般]、[專案和方案]](https://msdn.microsoft.com/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)。

 **預設語言**指定專案的預設語言。 系統會將使用者的慣用語言指定為控制台 [時鐘、語言和區域] 中選取的語言。 藉由指定專案預設語言，可確保當使用者的慣用語言不符合應用程式所提供的語言資源時，會使用指定的預設語言資源。

## <a name="debug-page"></a>偵錯頁面
 您可以使用下列選項，來設定專案中偵錯行為的屬性。

> [!NOTE]
> 有些選項僅適用於 Windows 市集應用程式。

 **要啟動的偵錯工具**指定偵錯工具的預設主控制項。

- 選取 [本機電腦]，在 Visual Studio 主機電腦上啟動應用程式。 如需詳細資訊，請參閱[在本機電腦上執行應用程式](http://go.microsoft.com/fwlink/?LinkId=234912)。

- 選取 [模擬器]，在模擬器中啟動應用程式。 如需詳細資訊，請參閱[在模擬器中執行應用程式](http://go.microsoft.com/fwlink/?LinkId=234913)。

- 選取 [遠端電腦]，在遠端電腦上啟動應用程式。 如需遠端偵錯的詳細資訊，請參閱[在遠端電腦上執行應用程式](http://go.microsoft.com/fwlink/?LinkId=234914)。

  **啟動應用程式**指定當您按下 F5 或按一下 [ **Debug**]、[**開始進行調試**程式] 時，是否要啟動應用程式。 選取 [是] 啟動應用程式；否則選取 [否]。 如果選取 [否]，即使您使用不同的方法啟動應用程式，還是可以對它進行偵錯。

  **偵錯工具類型**指定要進行 debug 錯的程式碼類型。 選取 [僅限指令碼] 以偵錯 JavaScript 程式碼。 選取 [僅限 Managed] 以偵錯由通用語言執行平台所管理的程式碼。 選取 [僅限原生] 以偵錯 C++ 程式碼。 選取 [機器碼加指令碼] 以偵錯 C++ 和 JavaScript。 選取 [混合 (Managed 和原生)] 以偵錯 Managed 和 C++ 程式碼。

  **允許區域網路回送**指定是否允許存取 IP 回送位址以進行應用程式測試。 如果用戶端應用程式與執行中伺服器應用程式是在同一部電腦上，請選取 [是] 允許使用回送位址；否則選取 [否]。 只有在 [要啟動的偵錯工具] 屬性設定為 [遠端電腦] 時，才能使用這個屬性。

  **電腦名稱稱**指定要裝載偵錯工具的遠端電腦名稱稱。 只有在 [要啟動的偵錯工具] 設定為 [遠端電腦] 時，才能使用這個屬性。

  **需要驗證**指定遠端電腦是否需要驗證。 只有在 [要啟動的偵錯工具] 設定為 [遠端電腦] 時，才能使用這個屬性。
