---
title: 管理組件和資訊清單簽署
description: 瞭解強式名稱簽署的優點，這會為軟體元件提供全域唯一的身分識別。
ms.custom: SEO-VS-2020
ms.date: 02/17/2017
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 709a5a64164ed6c80c29a8e554d2b07050e18339
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886518"
---
# <a name="manage-assembly-and-manifest-signing"></a>管理組件和資訊清單簽署

強式名稱簽署提供軟體元件的全域唯一識別。 強式名稱用以保證組件無法為他人作為詐騙之用，並確定元件的相依性和組態陳述式會對應到正確的元件和元件版本。

強式名稱是由組件的身分識別 (簡單文字名稱、版本號碼及文化特性資訊)，加上公開金鑰語彙基元和數位簽章所組成。

如需在 Visual Basic 和 C# 專案中簽署組件的資訊，請參閱[建立和使用強式名稱的組件](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)。

如需在 c + + 專案中簽署元件的相關資訊，請參閱 [強式名稱的元件 (c + +/cli) ](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)。

> [!NOTE]
> 強式名稱簽章無法保護組件免受反向工程的威脅。 若要防止反向工程，請參閱 [Dotfuscator Community](dotfuscator/index.md)。

## <a name="asset-types-and-signing"></a>資產類型和簽署

您可以簽署 .NET 組件和應用程式資訊清單：

- 可執行檔 (*.exe*)

- 應用程式資訊清單 (*.exe.manifest*)

- 部署資訊清單 (*.application*)

- 共用的元件組件 (*.dll*)

簽署下列資產類型：

1. 組件，如果您想要將它們部署到全域組件快取 (GAC)。

2. ClickOnce 署應用程式和部署資訊清單。 Visual Studio 根據預設可簽署這些應用程式。

3. 主要 Interop 組件，用於 COM 互通性。 從 COM 類型程式庫建立主要 Interop 組件時，TLBIMP 公用程式會強制執行強式命名。

一般來說，您不應該簽署可執行檔。 強式名稱元件無法參考與應用程式一起部署的非強式名稱元件。 Visual Studio 不簽署應用程式可執行檔，而是改為簽署應用程式資訊清單，指向弱式命名的可執行檔。 避免簽署應用程式的私用元件，因為簽署會使得相依性更難以管理。

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>如何簽署 Visual Studio 中的組件

使用 [專案屬性] 視窗的 [簽署] 索引標籤來簽署應用程式或元件 (以滑鼠右鍵按一下 [方案總管] 中的專案節點，然後選取 [屬性])。 選取 [簽署] 索引標籤，然後選取 [簽署組件] 核取方塊。

指定金鑰檔。 如果您選擇建立新的金鑰檔，新的金鑰檔一律會使用 *.pfx* 格式建立。 您需要新檔案的名稱和密碼。

> [!WARNING]
> 您應該一律以密碼保護金鑰檔，以防止他人使用您的金鑰檔。 您也可以使用提供者或憑證存放區來保護您的金鑰。

您也可以指向已經建立的金錀。 如需建立金鑰的詳細資訊，請參閱[如何：建立公開/私密金鑰組](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)。

如果您只能存取公開金鑰，您可以使用延遲簽署，稍後再指派金鑰。 選取 [僅延遲簽署] 核取方塊以啟用延遲簽署。 延遲簽署的專案不會執行，且無法進行偵錯。 不過，您可以搭配使用 [Sn.exe 強式名稱工具](/dotnet/framework/tools/sn-exe-strong-name-tool)與 `-Vr` 選項，在開發期間略過驗證。

如需簽署資訊清單的資訊，請參閱[如何：簽署應用程式和部署資訊清單](../ide/how-to-sign-application-and-deployment-manifests.md)。

## <a name="see-also"></a>另請參閱

- [強式名稱組件](/dotnet/framework/app-domains/strong-named-assemblies)
- [強式名稱組件 (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
