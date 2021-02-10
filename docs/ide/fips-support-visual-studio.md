---
title: Visual Studio 對 FIPS 的支援
titleSuffix: ''
description: 瞭解 Visual Studio 如何支援適用于 Windows、Azure 和 .NET 的聯邦資訊處理標準發行前140-2 核准模式。
ms.custom: SEO-VS-2020
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d6cb0d2bbcb1ec1d13f5916a7c2b1cd97824fb5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945535"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Visual Studio 支援的作業的 FIPS 140-2 核准模式

從 [16.4 版](/visualstudio/releases/2019/release-notes-v16.4/)開始，Visual Studio 2019 支援適用于 Windows、Azure 和 .net 的聯邦資訊處理標準 (FIPS) 發行集140-2 核准模式。 而且，在 [16.5 版](/visualstudio/releases/2019/release-notes-archive-v16.5)中，當您開發以 [遠端 Linux 系統為目標的 c + + 應用程式](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)時，Visual Studio 現在支援 FIPS 140-2 核准的作業模式。

若要設定 Visual Studio 的 FIPS 140-2 核准模式，請 [安裝 .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) ，然後啟用群組原則設定 [ **系統密碼編譯：使用符合 FIPS 規範的演算法進行加密、雜湊和簽署**]。

如需有關作業的 FIPS 140-2 核准模式及如何啟用的詳細資訊，請參閱 [fips 140-2 驗證](/windows/security/threat-protection/fips-140-validation/)。

> [!NOTE]
> 您用來為非 Microsoft 平臺（例如 iOS 或 Android）開發應用程式的工具，可能不會使用符合 FIPS 規範的演算法。 您安裝的 Visual Studio 或延伸模組隨附的協力廠商軟體，也可能不會使用符合 FIPS 規範的演算法。 而且， [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) 解決方案的開發並不支援 FIPS 140-2 核准的作業模式。

## <a name="next-steps"></a>下一步

若要深入瞭解 Visual Studio 和其他 Microsoft 產品和服務的 FIPS 140-2 核准模式，請參閱下列連結：

- [Visual Studio：使用 c + + 設定符合 FIPS 標準的安全遠端 Linux 開發](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows：系統密碼編譯和使用符合 FIPS 規範的演算法進行加密、雜湊和簽署](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core： FIPS 合規性](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>另請參閱

[保護應用程式](securing-applications.md)