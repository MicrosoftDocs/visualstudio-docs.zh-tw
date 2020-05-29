---
title: 對 FIPS 140-2 核准的作業模式 Visual Studio 支援
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d06204fd1ef6ee2deb5eadc514af1ede8ae9bb6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180489"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>對 FIPS 140-2 核准的作業模式 Visual Studio 支援

從[16.4 版](/visualstudio/releases/2019/release-notes-v16.4/)開始，Visual Studio 2019 支援聯邦資訊處理標準（FIPS）發行集 140-2 Windows、Azure 和 .net 已核准的操作模式。 而在[16.5 版](/visualstudio/releases/2019/release-notes-archive-v16.5)中，當您開發以[遠端 Linux 系統為目標的 c + + 應用程式](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)時，Visual Studio 現在支援 FIPS 140-2 核准的作業模式。

若要設定 Visual Studio 的 FIPS 140-2 核准模式，請[安裝 .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) ，然後啟用群組原則設定 [**系統密碼編譯：使用 FIPS 相容的演算法進行加密、雜湊及簽**章]。

如需有關 FIPS 140-2 核准的作業模式和如何啟用的詳細資訊，請參閱[fips 140-2 驗證](/windows/security/threat-protection/fips-140-validation/)。

> [!NOTE]
> 您用來針對非 Microsoft 平臺（例如 iOS 或 Android）開發應用程式的工具，可能不會使用符合 FIPS 規範的演算法。 隨附在 Visual Studio 或延伸模組中的協力廠商軟體，也可能不會使用符合 FIPS 規範的演算法。 而且， [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/)解決方案的開發不支援以 FIPS 140-2 核准模式運作。

## <a name="next-steps"></a>後續步驟

若要深入瞭解 Visual Studio 和其他 Microsoft 產品和服務之 FIPS 140-2 核准的作業模式，請參閱下列連結：

- [Visual Studio：使用 c + + 設定 FIPS 相容的安全遠端 Linux 開發](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows：系統加密和使用 FIPS 相容演算法進行加密、雜湊和簽署](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core： FIPS 合規性](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>另請參閱

[保護應用程式](securing-applications.md)
