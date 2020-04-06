---
title: VS包註冊 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a05dec8fbef40143f31f2c0ac484824717ea2e32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703926"
---
# <a name="vspackage-registration"></a>VSPackage 註冊
VSPackages[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必須 通知已安裝並應載入它們。 此過程通過在註冊表中寫入資訊來完成。 這是安裝程式的典型工作。

> [!NOTE]
> 在 VSPackage 開發期間,使用自註冊是公認的做法。 但是,[!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)]合作夥伴不能使用自註冊作為設置的一部分來運送其產品。

 Windows 安裝程式包中的註冊表項通常在註冊表表中創建。 您還可以在註冊表表中註冊檔副檔名。 但是,Windows 安裝程式透過程式設計標識碼 (ProgId)、類、擴展和動詞表提供內建支援。 有關詳細資訊,請參閱[資料庫表](/windows/desktop/Msi/database-tables)。

 請確保您的註冊表項與適合所選並行策略的元件相關聯。 例如,共用檔的註冊表項應與該檔的 Windows 安裝程式元件關聯。 同樣,特定於版本的檔的註冊表項應與該檔的元件關聯。 否則,為一個版本安裝或卸載 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可能會中斷其他版本的 VSPackage。 有關詳細資訊,請參閱[支援可視化工作室的多個版本](../../extensibility/supporting-multiple-versions-of-visual-studio.md)。

> [!NOTE]
> 管理註冊的最簡單方法是在同一檔中使用相同的數據進行開發人員註冊和安裝時間註冊。 例如,某些安裝程式開發工具可以在生成時使用 .reg 格式的檔。 如果開發人員維護 .reg 檔以進行自己的日常開發和調試,則這些相同的檔可以自動包含在安裝程式中。 如果無法自動共用註冊數據,則必須確保安裝程式的註冊數據副本是最新的。

## <a name="registering-unmanaged-vspackages"></a>註冊非託管 VS 套件
 非託管 VSPackage(包括由 Visual Studio 套件樣本產生的包包)使用 ATL 樣式的 .rgs 檔案來儲存註冊資訊。 .rgs 檔案格式特定於 ATL,通常不能按設備使用安裝創作工具。 VSPackage 安裝程式的註冊資訊必須單獨維護。 例如,開發人員可以將 .reg 格式的檔與 .rgs 檔更改同步。 .reg 檔案可以與 RegEdit 合併以進行開發工作,也可以由安裝程式使用。

## <a name="registering-managed-vspackages"></a>註冊託管 VS 套件
 RegPkg 工具從託管 VSPackage 讀取註冊屬性,可以將資訊直接寫入註冊表,也可以編寫安裝程式可以使用的 .reg 格式檔。

> [!NOTE]
> RegPkg 工具不可再分發,不能用於在用戶的系統上註冊 VSPackage。

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>為什麼 VS 套件不應在安裝時自行註冊
 您的 VSPackage 安裝程式不應依賴自註冊。 乍一看,僅在 VSPackage 本身中保留 VSPackage 的註冊表值似乎是個好主意。 鑒於開發人員需要可用於其日常工作和測試的註冊表值,因此避免在安裝程式中維護註冊表數據的單獨副本是有意義的。 安裝程式可以依靠 VSPackage 本身來寫入註冊表值。

 雖然理論上是好的,但自我註冊有幾個缺陷,使其不適合 VSPackage 安裝:

- 正確支援安裝、卸載、安裝回滾和卸載回滾需要針對每個通過調用 RegPkg 自行註冊的託管 VSPackage 編寫四個自定義操作。

- 並行支援的方法可能需要編寫四個自定義操作,針對[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的每個受支援的版本調用 RegSvr32 或 RegPkg。

- 具有自註冊模組的安裝無法安全地回滾,因為無法說明其他功能或應用程式是否使用自註冊密鑰。

- 自註冊的 DLL 有時連結到不存在或版本錯誤的輔助 DLL。 相反,Windows 安裝程式可以使用註冊表表註冊 DLL,而註冊表表不依賴於系統的當前狀態。

- 如果元件既指定為來自源的運行,又列在 SelfReg 表中,則可以拒絕對網路資源(如類型庫)的訪問。 這可能導致在管理安裝期間安裝元件失敗。

## <a name="see-also"></a>另請參閱
- [Windows 安裝程式](/windows/desktop/Msi/windows-installer-portal)
- [託管包註冊](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
