---
title: VSPackage 註冊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44114ccdc4a0873887d48c3d191506f10cc3eaf3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722006"
---
# <a name="vspackage-registration"></a>VSPackage 註冊
Vspackage 必須建議已安裝且應載入的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 此程式是藉由在登錄中寫入資訊來完成。 這是安裝程式的一般作業。

> [!NOTE]
> 這是在 VSPackage 開發期間，使用自我註冊的已接受做法。 不過，[!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] 合作夥伴無法在安裝過程中使用自我註冊來運送其產品。

 Windows Installer 套件中的登錄專案通常會在登錄表中進行。 您也可以在登錄表中註冊副檔名。 不過，Windows Installer 透過程式設計識別碼（ProgId）、類別、延伸模組和動詞資料表來提供內建支援。 如需詳細資訊，請參閱[資料庫資料表](/windows/desktop/Msi/database-tables)。

 請確定您的登錄專案與適用于您所選並存策略的元件相關聯。 例如，共用檔案的登錄專案應該與該檔案的 Windows Installer 元件相關聯。 同樣地，版本特定檔案的登錄專案應該與該檔案的元件相關聯。 否則，安裝或卸載某個版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的 VSPackage 可能會在其他版本中中斷您的 VSPackage。 如需詳細資訊，請參閱[支援多個版本的 Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)。

> [!NOTE]
> 管理註冊最簡單的方式，就是在開發人員註冊和安裝階段註冊時，在相同檔案中使用相同的資料。 例如，某些安裝程式開發工具可以在建立時使用 .reg 格式的檔案。 如果開發人員維護 .reg 檔案以進行自己的日常開發和偵測，則這些相同的檔案可以自動包含在安裝程式中。 如果您無法自動共用註冊資料，您必須確定安裝程式的註冊資料複本是最新的。

## <a name="registering-unmanaged-vspackages"></a>註冊非受控 Vspackage
 非受控 Vspackage （包括 Visual Studio 封裝範本所產生的）會使用 ATL 樣式的 .rgs 檔案來儲存註冊資訊。 .Rgs 檔案格式專屬於 ATL，而且通常無法由安裝 authoring tool 以現有方式取用。 您必須分別維護 VSPackage 安裝程式的註冊資訊。 例如，開發人員可以讓 .reg 格式的檔案與 .rgs 檔案的變更保持同步。 .Reg 檔案可以與 RegEdit 合併以進行開發工作，或安裝程式所使用。

## <a name="registering-managed-vspackages"></a>正在註冊受控 Vspackage
 RegPkg 工具會從 managed VSPackage 讀取註冊屬性，並且可以直接將資訊寫入登錄，或寫入可由安裝程式取用的 .reg 格式檔案。

> [!NOTE]
> RegPkg 工具不可轉散發，也無法用來在使用者的系統上註冊 VSPackage。

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>為什麼 Vspackage 不應在安裝時自行註冊
 您的 VSPackage 安裝程式不應依賴自我註冊。 乍看之下，只將 VSPackage 的登錄值保留在 VSPackage 本身，似乎是個不錯的主意。 假設開發人員需要可用於其例行工作和測試的登錄值，則避免在安裝程式中維護不同的登錄資料複本是合理的。 安裝程式可以依賴 VSPackage 本身來寫入登錄值。

 理論上，自我註冊有幾個缺點，使它不適合用于 VSPackage 安裝：

- 正確支援安裝、卸載、安裝復原和卸載復原，需要您為每個透過呼叫 RegPkg 而自行註冊的受控 VSPackage，撰寫四個自訂動作。

- 並存支援的方法可能會要求您撰寫四個自訂動作，針對每個支援的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]版本叫用 RegSvr32 或 RegPkg。

- 無法安全地復原具有自我註冊模組的安裝，因為沒有方法可以通知其他功能或應用程式是否使用自我註冊的金鑰。

- 自我註冊的 Dll 有時會連結至不存在或版本錯誤的輔助 Dll。 相反地，Windows Installer 可以使用登錄資料表來註冊 Dll，而不會相依于系統的目前狀態。

- 如果元件同時指定為從來源執行且列于 SelfReg 資料表中，則自我註冊程式碼可以拒絕存取網路資源（例如類型程式庫）。 這可能會導致元件在系統管理安裝期間失敗。

## <a name="see-also"></a>請參閱
- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [受控套件註冊](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)