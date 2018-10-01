---
title: VSPackage 註冊 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73a2dd2288ae54c184405793323cd3084b90e35a
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495280"
---
# <a name="vspackage-registration"></a>VSPackage 註冊
Vspackage 必須告知[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]它們已安裝，且應該會載入。 此程序，即可將資訊寫入登錄中。 這是典型的工作，安裝程式。  
  
> [!NOTE]
>  可接受的做法是使用自助式註冊 VSPackage 開發期間。 不過，[!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)]夥伴就無法出貨產品安裝程式的過程中使用自我登錄。  
  
 登錄資料表通常進行 Windows 安裝程式封裝中的登錄項目。 您也可以註冊副檔名登錄資料表中。 不過，Windows 安裝程式會提供內建支援，透過程式設計識別項 (ProgId)、 類別、 延伸與動詞命令的資料表。 如需詳細資訊，請參閱 <<c0> [ 資料庫資料表](/windows/desktop/Msi/database-tables)。  
  
 請確定您的登錄項目是適用於您所選擇的並排顯示策略的元件相關聯。 例如，共用檔案的登錄項目應該與該檔案的 Windows 安裝程式元件相關聯。 同樣地，版本特定檔案的登錄項目應該與該檔案的元件相關聯。 否則，安裝或解除安裝一個版本的 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可能會中斷其他版本的 VSPackage。 如需詳細資訊，請參閱[支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  管理註冊的最簡單方式是在相同的檔案中使用相同的資料，開發人員註冊和安裝階段註冊。 比方說，某些安裝程式開發工具也可以使用.reg 格式檔案，在建置階段。 如果開發人員維護.reg 檔案進行日常開發和偵錯時，這些相同的檔案可以包含在安裝程式自動。 如果您不能自動共用註冊資料時，您必須確定安裝程式之複本的註冊資料是最新。  
  
## <a name="registering-unmanaged-vspackages"></a>正在登錄 Unmanaged 的 Vspackage  
 （包括 Visual Studio Package 範本所產生） 的 unmanaged 的 Vspackage 會使用 ATL 樣式.rgs 檔案來儲存註冊資訊。 .Rgs 檔案格式特有 ATL，且通常無法使用以-為撰寫工具的安裝。 VSPackage 安裝程式的註冊資訊必須分開維護。 比方說，開發人員可以保留檔案格式為.reg.rgs 同步檔案變更。 .Reg 檔案可以合併使用 RegEdit 的開發工作，或由安裝程式。  
  
## <a name="registering-managed-vspackages"></a>登錄 Managed 的 Vspackage  
 RegPkg 工具會讀取的登錄屬性從 managed VSPackage，可以是直接將資訊寫入登錄或可供安裝程式的寫入.reg 格式檔案。  
  
> [!NOTE]
>  RegPkg 工具不是可轉散發套件，並不能用來註冊 VSPackage 使用者的系統上。  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>為什麼 Vspackage 應該自我註冊在安裝階段  
 VSPackage 的安裝程式不應依賴自我登錄。 第一眼，只有在本身的 VSPackage 中保留 VSPackage 的登錄值看起來像是個不錯的主意。 提供開發人員在其日常工作需要可用的登錄值，並測試，所以合理避免維護另一份安裝程式中的登錄資料。 安裝程式都可以依賴 VSPackage 本身要寫入登錄值。  
  
 好的理論上，同時自我登錄會有讓它更適合使用 VSPackage 安裝的幾個缺點：  
  
-   正確支援安裝、 解除安裝、 安裝復原和解除安裝回復要求您撰寫自我呼叫 RegPkg 註冊每個 managed VSPackage 的四個自訂動作。  
  
-   並排顯示支援的方法可能會要求您撰寫 RegSvr32 或 RegPkg 叫用的每個支援版本的四個自訂動作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   自我登錄模組的安裝無法安全地復原，因為沒有任何方法，告訴自我登錄機碼由其他功能或應用程式。  
  
-   自我登錄的 Dll 有時會連結到輔助不存在或版本不正確的 Dll。 相反地，Windows 安裝程式可以登錄 Dll 登錄資料表使用不會相依於系統的目前狀態。  
  
-   自我登錄程式碼可以存取網路資源，例如型別程式庫，如果某個元件有同時指定為執行從來源和 SelfReg 表列出會被拒絕。 這會導致系統管理安裝期間失敗元件的安裝。  
  
## <a name="see-also"></a>另請參閱  
 [Windows 安裝程式](/windows/desktop/Msi/windows-installer-portal)   
 [受管理的套件註冊](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)