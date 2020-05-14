---
title: 創作 Windows 安裝程式套件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d30c0e2b3b375e6e0efedddd3a017fbfb8646a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710032"
---
# <a name="author-a-windows-installer-package"></a>編寫 Windows 安裝程式套件
數據驅動 Windows 安裝程式模型。 例如,您不是編寫過程腳本來複製檔和編寫註冊表項,而是在包含檔和註冊表數據的資料庫表中創作行和列。

## <a name="database-entries"></a>資料庫項目
要安裝 VSPackage,Windows 安裝程式套件必須包含資料庫項目才能執行以下任務:

- 搜索系統以查找 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援的版本(使用包括應用搜尋、CompLocator、RegLocator、DrLocator 和簽名在內的 Windows 安裝程式表)。

- 如果未安裝支援的版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]或不符合 VS 包的另一個系統要求(使用啟動條件表),則取消安裝。

- 安裝 VSPackage 和從屬檔(使用目錄、元件和檔表)。

- 向註冊表添加 VSPackage 的適當資訊(使用註冊表表)。

- 通過調用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**devenv.exe /安裝程式**(使用自訂操作表)將 VSPackage 整合到其中。

有關詳細資訊,請參閱[Windows 安裝程式](/windows/desktop/Msi/windows-installer-portal)。

## <a name="setup-tools"></a>設定工具
各種第三方設置工具為 Windows 安裝程式包提供了開發環境。 提供以下免費工具:

- 安裝護盾限量版

   您可以通過視覺化工作室**新專案**對話框獲得有限版本的安裝程式。 展開**其他項目類型**,然後選擇 **「設定和部署**」。 選擇安裝護盾範本。

- Windows 安裝程式 XML 工具集

   Windows 安裝程式 XML (WiX) 工具集從 XML 源檔生成 Windows 安裝程式套件。 WiX 工具集是Microsoft開源專案。 你可以從[Wix工具集](https://sourceforge.net/projects/wix/)下載原始程式碼和可執行檔。

   有關[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用 整合到 中的商業[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]產品, 請參閱[可視化工作室市場](https://marketplace.visualstudio.com/)。

## <a name="see-also"></a>另請參閱
- [使用 Windows 安裝程式安裝 VS 套件](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
