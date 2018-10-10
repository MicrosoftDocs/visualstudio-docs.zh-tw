---
title: Android 版 Visual Studio 模擬器的系統需求 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
caps.latest.revision: 7
ms.author: crdun
manager: crdun
ms.openlocfilehash: 2bf6251b8152224b521f60b0ec1694e03adeb9b1
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880465"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>System requirements for the Visual Studio Emulator for Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[Visual Studio emulator for Android 的系統需求](https://docs.microsoft.com/visualstudio/cross-platform/system-requirements-for-the-visual-studio-emulator-for-android)。  
  
  
Visual Studio Emulator for Android 是以虛擬機器形式在 Hyper-V (Windows 8 及更新版本的虛擬化技術) 上執行。 若要執行模擬器，您的電腦必須符合執行 Hyper-V 的需求 (如本主題所述)。  
  
 安裝程式會在您安裝模擬器時嘗試以無訊息方式設定這些必要條件。 安裝程式成功設定必要條件時，模擬器就會依照預期方式運作。 否則，您可能需要手動啟用這些必要條件。 如果您需要手動設定必要條件，則步驟和工具與 [這裡](https://msdn.microsoft.com/library/windows/apps/jj863509\(v=vs.105\).aspx) 針對 Windows Phone 模擬器所述的步驟相同。  
  
> [!IMPORTANT]
>  模擬器的安裝程式會檢查執行 Visual Studio Emulator for Android 的必要條件。 如果必要條件不存在，則會顯示警告，但安裝時不需要這些必要條件。  
  
 此主題包括下列各節。  
  
-   [快速檢查清單](#Checklist)  
  
-   [系統需求](#System)  
  
-   [網路需求](#Network)  
  
-   [Hyper-V 需求](#HyperV)  
  
-   [不支援從可開機的 VHD 執行模擬器](#BootableVHD)  
  
-   [Hyper-V 需要未壓縮和未加密的檔案](#Files)  
  
##  <a name="Checklist"></a> 快速檢查清單  
 以下是 Visual Studio Emulator for Android 執行需求的快速檢查清單。 如需詳細資訊，請參閱本主題中的後續章節。  
  
 系統需求  
  
-   Hyper-V 支援 (請參閱下面的 Hyper-V 需求)  
  
-   6 GB 或以上的 RAM。  
  
-   64 位元版的 Windows 8、Windows 8.1、Windows10 或更高的 Pro 版本  
  
-   支援 SSSE3 或更新版本的處理器。  
  
 網路需求  
  
-   DHCP  
  
-   自動設定的 DNS 和閘道設定  
  
 Hyper-V 需求  
  
-   在 BIOS 中，必須支援下列功能：  
  
    -   硬體協助虛擬化  
  
    -   第二層位址轉譯 (SLAT)  
  
    -   硬體型資料執行防止 (DEP)  
  
-   在 Windows 中，Hyper-V 必須啟用並執行。  
  
-   您必須是本機 Hyper-V Administrators 群組的成員。  
  
##  <a name="System"></a> 系統需求  
 您的電腦必須符合下列需求：  
  
-   HYPER-V 支援 (請參閱 [Hyper-V 需求](#HyperV))  
  
-   6 GB 或以上的 RAM。  
  
-   64 位元版的 Windows 8、Windows 8.1、Windows10 或更高的 Pro 版本。  
  
 若要檢查 RAM 和 Windows 的需求，請選擇 [控制台] 中的 [系統及安全性]，然後選擇 [系統]。  
  
 ![確認系統需求](../cross-platform/media/android-emu-system-requirements.png "Android_Emu_System_Requirements")  
  
##  <a name="Network"></a> 網路需求  
 您的網路必須符合下列需求：  
  
-   DHCP  
  
     模擬器需要 DHCP，因為它會將本身設定為網路上具有本身 IP 位址的個別裝置。  
  
-   自動設定的 DNS 和閘道設定  
  
     您無法手動設定模擬器的 DNS 和閘道設定。  
  
 若要疑難排解模擬器中的網路問題，請參閱下列主題：  
  
-   [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)  
  
##  <a name="HyperV"></a> Hyper-V 需求  
 BIOS 中的 Hyper-V 需求  
  
 您電腦的 BIOS 必須支援下列需求，而且必須啟用它們：  
  
-   硬體協助虛擬化  
  
-   第二層位址轉譯 (SLAT)  
  
-   硬體型資料執行防止 (DEP)  
  
 Windows 中的 Hyper-V 需求  
  
 當您的電腦及 BIOS 已設定為支援 HYPER-V 時，安裝程式會啟用並啟動 HYPER-V。 否則，您可能需要手動啟用這些需求。  
  
|需求|如何檢查和啟用此需求|  
|-----------------|----------------------------------------------|  
|必須安裝 Hyper-V|遵循 [啟用適用於 Windows Phone 模擬器的 HYPER-V](https://msdn.microsoft.com/library/windows/apps/jj863509\(v=vs.105\).aspx)所使用的相同指示。<br /><br /> 在 [服務] 嵌入式管理單元中，檢查 [Hyper-V 虛擬機器管理]  服務的狀態。|  
|必須執行 Hyper-V。|如需管理服務的詳細資訊，請參閱下列主題：<br /><br /> -   [啟動、停止、暫停、繼續或重新啟動服務](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [設定如何啟動服務](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|  
  
 您必須是本機 Hyper-V Administrators 群組的成員。  
  
 若要執行 Visual Studio Emulator for Android，而不週期性提示提高權限，則您必須是本機 Hyper-V Administrators 群組的成員。 如果您在安裝 SDK 時已經是電腦的本機系統管理員，則 SDK 的安裝程式會將您新增至 Hyper-V Administrators 群組。 否則，您可能需要手動啟用此需求。  
  
 執行模擬器時，如果您還不是 Hyper-V Administrators 群組的成員，則系統會提示您加入該群組 (對話方塊指的是 Windows Phone 模擬器)。 加入此群組需要有系統管理員權限。  
  
> [!IMPORTANT]
> 加入此群組之後，請登出或重新開機，以讓變更生效。  
  
 ![加入 Hyper&#45;V 系統管理員安全性群組](../cross-platform/media/android-emu-hyperv-admin.png "Android_Emu_HyperV_Admin")  
  
 若要手動將您自己加入群組，請開啟 [本機使用者和群組] 嵌入式管理單元。
 
##  <a name="BootableVHD"></a> 不支援從可開機的 VHD 執行模擬器  
 如果您在從可開機的 VHD 執行 Windows 時，嘗試在 Visual Studio Emulator for Android 上執行應用程式，則模擬器通常需要數分鐘的時間才能啟動，或無法啟動。 無法啟動模擬器時，您會看到下列訊息：應用程式部署失敗。 請重試。  
  
 不支援這個組態。 如需相關問題資訊，請參閱 [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)。  
  
##  <a name="Files"></a> Hyper-V 需要未壓縮和未加密的檔案  
 在以 NTFS 檔案系統設定的硬碟上，Hyper-V 所使用的虛擬硬碟檔案必須為未壓縮和未加密。 請確定未壓縮或加密下列目錄：  
  
-   %localappdata%\Microsoft\XDE  
  
-   C:\Program Files (x86)\Microsoft Emulator Manager  
  
-   C:\Program Files (x86)\Microsoft Visual Studio Emulator for Android  
  
-   %localappdata%\Microsoft\VisualStudioEmulator  
  
 在 ReFS 檔案系統上，虛擬硬碟檔案不得設定完整性位元。  
  
## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>硬體圖形轉送 (OpenGL ES 支援) 需求  
 為了讓模擬器模擬 GPU 呼叫 (例如 OpenGL ES 所使用的呼叫)，您的電腦必須具有已安裝適當 DirectX 驅動程式的 DirectX 相容 GPU。  
  
## <a name="see-also"></a>另請參閱  
 [進行 Android 版 Visual Studio 模擬器的疑難排解](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

