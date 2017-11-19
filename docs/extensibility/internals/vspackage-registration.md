---
title: "VSPackage 註冊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 263e2adf69aa479974a07dbb2acc2d4cd8f2a0dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="vspackage-registration"></a>VSPackage 註冊
Vspackage 必須告知可用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]確認他們已安裝，且應該會載入。 此程序被透過將資訊寫入登錄中。 這是安裝程式的典型的作業。  
  
> [!NOTE]
>  已接受的作法是使用自我登錄 VSPackage 開發期間。 不過，[!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)]夥伴就無法出貨他們的產品中使用自我登錄，安裝程序。  
  
 Windows Installer 封裝中的登錄項目通常會登錄資料表中。 您也可以註冊登錄資料表中的檔案副檔名。 不過，Windows Installer 提供內建支援，透過程式設計識別項 (ProgId)、 類別、 延伸模組和動詞命令的資料表。 如需詳細資訊，請參閱[資料庫資料表](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx)。  
  
 請確定您的登錄項目是與適用於您的選擇來並行策略元件相關聯。 例如，共用檔案的登錄項目應該與該檔案的 Windows Installer 元件相關聯。 同樣地，版本特定檔案的登錄項目應該與該檔案元件相關聯。 否則，安裝或解除安裝一個版本 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在其他版本中可能會破壞您的 VSPackage。 如需詳細資訊，請參閱[支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  管理登錄最簡單的方式是使用相同的資料相同的檔案中，開發人員註冊和安裝期間註冊。 比方說，某些安裝程式開發工具可能會在建置階段耗用.reg 格式檔案。 如果開發人員維護自己的日常開發的.reg 檔案並進行偵錯，這些相同的檔案可以包含在安裝程式自動。 如果您不會自動共用登錄資料，您必須確定安裝程式的註冊資料副本是最新。  
  
## <a name="registering-unmanaged-vspackages"></a>登錄 Unmanaged 的 Vspackage  
 Unmanaged 的 Vspackage （包括 Visual Studio 封裝範本所產生） 會使用 ATL 樣式.rgs 檔案來儲存註冊資訊。 .Rgs 檔案格式特有 ATL，且通常無法做為使用的是撰寫工具的安裝。 VSPackage 安裝程式的註冊資訊必須分開維護。 例如，開發人員可以保留檔案.reg 格式.rgs 同步檔案變更。 .Reg 檔案可以與 RegEdit 合併的開發工作，或由安裝程式。  
  
## <a name="registering-managed-vspackages"></a>註冊 Managed 的 Vspackage  
 RegPkg 工具會讀取的登錄屬性從 managed VSPackage，可以是直接將資訊寫入登錄或寫入.reg 格式檔案，可供安裝程式。  
  
> [!NOTE]
>  RegPkg 工具不是可轉散發套件，並不能用來註冊 VSPackage 也在使用者的系統上。  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>為什麼 Vspackage 不應自我註冊在安裝期間  
 您的 VSPackage 安裝程式不應依賴自我登錄。 第一眼看起來，只有在 VSPackage 本身中保留 VSPackage 的登錄值似乎是個好主意。 指定開發人員例行工作需要可用的登錄值，而且測試，因此才會避免維護個別的安裝程式中的登錄資料的複本。 安裝程式可以依賴 VSPackage 本身要寫入登錄值。  
  
 良好理論上，同時自我登錄會有數個有缺陷而使其適合 VSPackage 安裝：  
  
-   正確支援安裝、 解除安裝，安裝復原及復原解除安裝，需要撰寫呼叫 RegPkg 自行註冊每個 managed VSPackage 的四個自訂動作。  
  
-   並行所支援的方法可能會要求您撰寫自訂的 RegSvr32 或 RegPkg 叫用每個版本支援的四個動作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   使用自我登錄的模組安裝無法安全地復原，因為沒有任何要告訴自我登錄機碼由其他功能或應用程式的方法。  
  
-   自我登錄的 Dll 有時會連結至不存在或版本不正確的輔助 Dll。 相反地，Windows Installer 可以註冊 Dll 登錄資料表使用不會相依於目前的系統狀態。  
  
-   存取網路資源，例如類型程式庫中，如果元件是同時指定為從來源執行而且列於 SelfReg 資料表中，自我登錄程式碼可能會遭到拒絕。 這可能會導致元件失敗的系統管理安裝期間安裝。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Managed 的封裝註冊](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)