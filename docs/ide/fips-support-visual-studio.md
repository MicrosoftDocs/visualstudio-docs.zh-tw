---
title: 對 FIPS 140-2 批准的操作模式的視覺工作室支援
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06d147397a168bb78a31a8fbe6929d6c2184d080
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81386446"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>對 FIPS 140-2 批准的操作模式的視覺工作室支援

從[版本 16.4](/visualstudio/releases/2019/release-notes-v16.4/)開始,Visual Studio 2019 支援聯邦資訊處理標準 (FIPS) 出版物 140-2 批准的 Windows、Azure 和 .NET 的操作模式。 並且,使用[版本16.5,Visual](/visualstudio/releases/2019/release-notes-v16.5/)Studio現在支援FIPS 140-2批准的操作模式,當您開發[面向遠端 Linux 系統的C++應用程式](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)時。

要為 Visual Studio 設定 FIPS 140-2 批准的作業模式,[請安裝 .NET 框架 4.8,](https://dotnet.microsoft.com/download/dotnet-framework/net48)然後啟用組策略設定「**系統加密:使用符合 FIPS 的演算法進行加密、哈希和簽名**。

有關 FIPS 140-2 批准的操作模式以及如何啟用它的詳細資訊,請參閱[FIPS 140-2 驗證](/windows/security/threat-protection/fips-140-validation/)。

> [!NOTE]
> 用於為 iOS 或 Android 等非 Microsoft 平台開發應用的工具可能不使用符合 FIPS 的演演演算法。 Visual Studio 或安裝的擴展附帶的第三方軟體也可能不使用符合 FIPS 的演演演算法。 而且[,SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/)解決方案的開發不支援FIPS 140-2批准的操作模式。

## <a name="next-steps"></a>後續步驟

要瞭解有關 Visual Studio 和其他 Microsoft 產品和服務的 FIPS 140-2 批准的操作模式,請參閱以下連結:

- [視覺化工作室:使用C++設定符合 FIPS 的安全遠端 Linux 開發](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows:系統加密和使用符合 FIPS 的演算法進行加密、哈希和簽名](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET 核心:FIPS 合規性](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>另請參閱

[保護應用程式](securing-applications.md)