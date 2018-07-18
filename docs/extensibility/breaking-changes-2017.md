---
title: Visual Studio 2017 擴充中的重大變更 |Microsoft 文件
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bff9c97b052f359f3d03e12093b1cdae86d5dfbd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107172"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Visual Studio 2017 擴充中的變更

使用 Visual Studio 2017，我們提供[更快、 輕量型的 Visual Studio 安裝經驗](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer)，同時提供使用者的工作負載和功能的更大的選擇以減少使用者在系統上，Visual Studio 的影響所安裝。 若要支援這些增強功能，我們已經變更擴充性模型，並有一些重大變更對 Visual Studio 擴充性。 本文件將描述這些變更，以及可以做什麼，若要解決這些問題的技術詳細資料。 請注意一些資訊的時間點的實作詳細資料，並稍後可能會變更。

## <a name="changes-affecting-vsix-format-and-installation"></a>VSIX 格式和安裝影響的變更

我們介紹 VSIX v3 （第 3 版） 格式，以支援輕量級安裝經驗。

VSIX 格式的變更包括：

* 安裝程式必要條件的宣告。 若要履行承諾的輕量型、 快速安裝 Visual Studio 中，安裝程式現在會對使用者提供更多組態選項。 如此一來，若要確保安裝的功能和擴充功能所需的元件，擴充功能會需要宣告及其相依性。
  * 取得與使用者必要的元件安裝為安裝擴充功能的一部分，會自動提供 Visual Studio 2017 安裝程式。
  * 嘗試安裝的不使用建立新的 VSIX v3 格式，即使它們已經標示為目標版本 15.0 其資訊清單中的擴充功能時，系統也會警告使用者。
* VSIX 格式的增強的功能。 履行[低影響的安裝](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install)也支援-並存安裝的 Visual studio，我們不會再將大部分的組態資料儲存至系統登錄中，移出 GAC 的 Visual Studio 特定組件。 我們也可以增加的功能的 VSIX 格式和 VSIX 安裝引擎，可讓您使用它，而非 MSI 或 EXE 來安裝您的擴充功能，針對某些安裝類型。

  新功能包括：

  * 指定 Visual Studio 執行個體的註冊。
  * 外的，於安裝[extensions 資料夾](set-install-root.md)。
  * 處理器架構的偵測。
  * 語言分隔語言組件相依性。
  * 安裝與[NGEN 支援](ngen-support.md)。

## <a name="building-an-extension-for-visual-studio-2017"></a>Visual Studio 2017 建置延伸模組

設計工具的工具來撰寫新的 VSIX v3 資訊清單格式現在已提供使用 Visual Studio 2017。 請參閱隨附的文件[How to： 將擴充性專案移轉至 Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)如使用設計工具或專案中進行手動更新的詳細資訊和開發 VSIX v3 延伸模組資訊清單。

## <a name="change-visual-studio-user-data-path"></a>變更： Visual Studio 使用者資料路徑

先前，只有一個安裝的每個主要版本的 Visual Studio 可能存在的每部電腦上。 若要支援的並存安裝 Visual Studio 2017，適用於 Visual Studio 的多個使用者資料路徑可能存在於使用者的電腦。

Visual Studio 處理序內執行的程式碼應該更新為使用 Visual Studio 設定管理員。 在 Visual Studio 處理序外執行的程式碼可以尋找特定的 Visual Studio 安裝的使用者路徑[遵循的指導方針](locating-visual-studio.md)。

## <a name="change-global-assembly-cache-gac"></a>變更： 全域組件快取 (GAC)

大部分的 Visual Studio 核心組件不會安裝到 GAC。 進行下列變更，讓 Visual Studio 處理序中執行的程式碼仍在執行階段尋找必要的組件。

> [!NOTE]
> [INSTALLDIR] 下面是指 Visual Studio 安裝根目錄。 VSIXInstaller.exe 會自動填入，但若要撰寫自訂部署的程式碼，請閱讀[尋找 Visual Studio](locating-visual-studio.md)。

* 只安裝至 GAC 的組件：
  * 這些組件現在安裝下 [INSTALLDIR] \Common7\IDE\, [INSTALLDIR] \Common7\IDE\PublicAssemblies 或 [INSTALLDIR] \Common7\IDE\PrivateAssemblies。 這些資料夾是 Visual Studio 處理序的探查路徑的一部分。
* 已安裝成非探查路徑，並置於 GAC 的組件：
  * 在 GAC 中的複本已從安裝程式移除。
  * 若要指定組件的程式碼基底項目，已加入.pkgdef 檔。

    例如: 
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    在執行階段，Visual Studio pkgdef 子系統會合併至 Visual Studio 處理序的執行階段組態檔 （在 [VSAPPDATA]\devenv.exe.config) 這些項目為[ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx)項目。 這是因為它可避免搜尋整個探查路徑，讓 Visual Studio 處理尋找組件的建議的方式。

### <a name="reacting-to-this-breaking-change"></a>這項重大變更對回應

* 如果您的擴充功能 Visual Studio 處理序內執行：
  * 您的程式碼將找不到 Visual Studio 核心組件。
  * 請考慮使用.pkgdef 檔來指定您如有必要的組件的路徑。
* 如果在 Visual Studio 處理序之外執行您的擴充功能：
  * 尋找 [INSTALLDIR] \Common7\IDE 下的 Visual Studio 核心組件，請考慮\,[INSTALLDIR] \Common7\IDE\PublicAssemblies 或 [INSTALLDIR] \Common7\IDE\PrivateAssemblies 使用組態檔或組件解析程式。

## <a name="change-reduce-registry-impact"></a>變更： 減少登錄的影響

### <a name="global-com-registration"></a>全域 COM 註冊

* 過去，Visual Studio 安裝 HKEY_CLASSES_ROOT 和 HKEY_LOCAL_MACHINE 登錄區，以支援原生 COM 註冊許多登錄機碼。 若要消除這種影響，Visual Studio 現在使用[免註冊啟動 COM 元件的](https://msdn.microsoft.com/en-us/library/ms973913.aspx)。
* 如此一來，大部分的 TLB / OLB / Visual Studio 預設不再安裝在 %programfiles (x86) %\Common Files\Microsoft Shared\MSEnv DLL 檔案。 使用 Visual Studio 主機處理序所使用的對應免註冊 COM 資訊清單，這些檔案現在會安裝 [INSTALLDIR] 下。
* 如此一來，依賴全域的 Visual Studio COM 介面的 COM 註冊的外部程式碼不會再尋找這些註冊。 Visual Studio 處理序內執行的程式碼不會看到差異。

### <a name="visual-studio-registry"></a>Visual Studio 登錄

* 先前，Visual Studio 安裝的 Visual Studio 特定機碼下系統的 HKEY_LOCAL_MACHINE 和 HKEY_CURRENT_USER 登錄區許多登錄機碼：
  * HKLM\Software\Microsoft\VisualStudio\\**版本**: MSI 安裝程式與每台機器擴充功能所建立的登錄機碼。
  * HKCU\Software\Microsoft\VisualStudio\\**版本**： 來儲存使用者特定設定的 Visual Studio 所建立的登錄機碼。
  * HKCU\Software\Microsoft\VisualStudio\\**版本**_Config： 一份以上版本，Visual Studio HKLM 鍵加上的登錄機碼從.pkgdef 檔案合併的擴充功能。
* 若要降低對登錄影響，Visual Studio 現在使用[RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx)函式儲存在私用二進位檔案中 [VSAPPDATA]\privateregistry.bin 下登錄機碼。 只有非常少數的 Visual Studio 特定索引鍵會保留在系統登錄。
* Visual Studio 處理序內部執行的現有程式碼不會受到影響。 Visual Studio 會在私人登錄重新導向 HKCU Visual Studio 特定機碼下的所有登錄作業。 讀取和寫入登錄中的其他位置將會繼續使用系統登錄。
* 外部程式碼必須載入並讀取此檔案的 Visual Studio 登錄項目。

### <a name="reacting-to-this-breaking-change"></a>這項重大變更對回應

* 外部程式碼應該轉換成的 COM 元件以及使用免註冊啟用。
* 外部元件可以找到 Visual Studio 位置[遵循的指導方針](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)。
* 我們建議使用的外部元件[外部設定管理員](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx)而不是直接到 Visual Studio 登錄機碼的讀取/寫入。
* 請檢查您的延伸模組所使用的元件是否已實作另一種技術的註冊。 例如，偵錯工具擴充功能可能是能夠充分利用新的[msvsmon JSON 檔案 COM 登錄](migrate-debugger-COM-registration.md)。
