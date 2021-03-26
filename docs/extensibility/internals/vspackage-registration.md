---
title: VSPackage 註冊 |Microsoft Docs
description: 深入瞭解 VSPackage 註冊，其中套件建議 Visual Studio 安裝這些套件，並在登錄中寫入資訊以載入這些套件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: afa2ac0f8608e7cafe8c465ea5ff0b8c0031dd58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069149"
---
# <a name="vspackage-registration"></a>VSPackage 註冊
Vspackage 必須建議 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 它們已安裝且應該載入。 這項程式的完成方式是在登錄中寫入資訊。 這是安裝程式的一般作業。

> [!NOTE]
> 在 VSPackage 開發期間，使用自我註冊是接受的做法。 不過， [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] 在安裝過程中，合作夥伴無法使用自我註冊來傳送產品。

 Windows Installer 套件中的登錄專案通常是在登錄表中進行。 您也可以在登錄表中註冊副檔名。 不過，Windows Installer 透過程式設計識別碼 (ProgId) 、類別、延伸和動詞資料表）提供內建支援。 如需詳細資訊，請參閱 [資料庫資料表](/windows/desktop/Msi/database-tables)。

 確定您的登錄專案與適用于您所選並存策略的元件相關聯。 例如，共用檔案的登錄專案應該與該檔案的 Windows Installer 元件相關聯。 同樣地，版本特定檔案的登錄專案應該與該檔案的元件相關聯。 否則，安裝或卸載其中一個版本的 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可能會中斷其他版本的 VSPackage。 如需詳細資訊，請參閱 [支援 Visual Studio 的多個版本](../../extensibility/supporting-multiple-versions-of-visual-studio.md)。

> [!NOTE]
> 管理註冊最簡單的方式，就是在相同的檔案中使用相同的資料來進行開發人員註冊和安裝時間註冊。 例如，某些安裝程式開發工具可以在組建階段使用 .reg 格式的檔案。 如果開發人員針對自己的日常開發和偵錯工具維護 .reg 檔案，則這些相同的檔案可以自動包含在安裝程式中。 如果您無法自動共用註冊資料，您必須確定安裝程式的註冊資料複本是最新的。

## <a name="registering-unmanaged-vspackages"></a>註冊非受控 Vspackage
 非受控 Vspackage (包括 Visual Studio 封裝範本所產生的) 使用 ATL 樣式的 .rgs 檔案來儲存註冊資訊。 .Rgs 檔案格式是 ATL 專屬的，而且通常無法由安裝 authoring tool 依原樣使用。 VSPackage 安裝程式的註冊資訊必須分開維護。 例如，開發人員可以讓 .reg 格式的檔案與 .rgs 檔案的變更保持同步。 .Reg 檔案可以與 RegEdit 合併以進行開發工作或安裝程式所使用。

## <a name="registering-managed-vspackages"></a>註冊 Managed Vspackage
 RegPkg 工具會從受控 VSPackage 讀取註冊屬性，並且可以直接將資訊寫入登錄或寫入可供安裝程式使用的 .reg 格式檔案。

> [!NOTE]
> RegPkg 工具無法轉散發，且無法用來在使用者的系統上註冊 VSPackage。

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Vspackage 在安裝時不應 Self-Register 的原因
 您的 VSPackage 安裝程式不應依賴自我註冊。 乍看之下，只在 VSPackage 本身保留 VSPackage 的登錄值似乎是個好主意。 由於開發人員需要可用的登錄值來進行例行工作和測試，因此避免在安裝程式中維護個別的登錄資料複本，是合理的。 安裝程式可以依賴 VSPackage 本身來寫入登錄值。

 在理論上，自我註冊有幾個缺點，讓它不適合用于 VSPackage 安裝：

- 正確支援安裝、卸載、安裝復原和卸載復原，需要您為每個由呼叫 RegPkg 的受控 VSPackage 撰寫四個自訂動作。

- 並行支援的方法，可能會要求您撰寫四個自訂動作，以針對每個支援的版本叫用 RegSvr32 或 RegPkg [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- 具有自我註冊模組的安裝無法安全地復原，因為沒有辦法告知自我註冊的金鑰是否由其他功能或應用程式使用。

- 自我註冊的 Dll 有時會連結至不存在或版本錯誤的輔助 Dll。 相反地，Windows Installer 可以使用登錄資料表註冊 Dll，而不會相依于系統目前的狀態。

- 如果元件同時指定為從來源執行，而且會列在 SelfReg 資料表中，則可能會拒絕自我註冊程式碼存取網路資源（例如類型程式庫）。 這可能會導致元件的安裝在系統管理安裝期間失敗。

## <a name="see-also"></a>另請參閱
- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [受控套件註冊](/previous-versions/bb166783(v=vs.100))