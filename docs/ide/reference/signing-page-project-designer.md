---
title: 專案設計工具、簽署頁
description: 您可以使用 [專案設計工具] 的 [簽署] 頁面來簽署應用程式和部署資訊清單，也可以簽署元件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f52d02407316fbc8f9a7b5e3db1c02a3566cda87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957578"
---
# <a name="signing-page-project-designer"></a>專案設計工具、簽署頁

使用 [專案設計工具]的 [簽署] 頁面可簽署應用程式和部署資訊清單，也可簽署組件 (強式名稱簽署)。

請注意，雖然簽署應用程式和部署資訊清單與簽署組件都是在 [簽署] 頁面上執行，但是這兩個工作的程序不同。

此外，金鑰檔資訊的儲存方式會與資訊清單簽署和組件簽署不同。 針對資訊清單簽署，金鑰資訊會儲存在您電腦的密碼編譯儲存資料庫和目前使用者的 Windows 憑證存放區中。 針對組件簽署，金鑰資訊只會儲存在您電腦的密碼編譯儲存資料庫中。

若要存取 [簽署] 頁面，請選取方案總管中的專案節點，然後按一下 [專案] 功能表上的 [屬性]。 [專案設計工具] 出現時，請按一下 [簽署] 索引標籤。

## <a name="application-and-deployment-manifest-signing"></a>應用程式和部署資訊清單簽署

[簽署 ClickOnce 資訊清單] 核取方塊

選取這個核取方塊，可使用公開/私密金鑰組來簽署應用程式和部署資訊清單。 如需做法的詳細資訊，請參閱[如何：簽署應用程式和部署資訊清單](../../ide/how-to-sign-application-and-deployment-manifests.md)。

[從存放區選取] 按鈕

可讓您從目前使用者的個人憑證存放區中選取現有憑證。 您可以選取下列其中一個憑證來簽署您的應用程式和部署資訊清單。

按一下 [從存放區選取] 會開啟 [選取憑證] 對話方塊，其中列出您個人憑證存放區中目前有效 (未到期) 的憑證，以及具有私密金鑰的憑證。 所選取憑證的用途應該包括程式碼簽署。

如果您按一下 [檢視憑證屬性]，則會顯示 [憑證詳細資料] 對話方塊。 這個對話方塊包含憑證的詳細資訊與其他選項。 您可以按一下 [深入了解憑證] 檢視其他說明資訊。

[從檔案選取] 按鈕

可讓您從現有金鑰檔中選取憑證。

按一下 [從檔案選取] 會開啟 [選取檔案] 對話方塊，以讓您選取憑證金鑰檔 (.pfx)。 這個檔案必須受密碼保護，而且不能位於您的個人憑證存放區中。

在 [輸入密碼以開啟檔案] 對話方塊中，輸入密碼來開啟憑證金鑰檔 (.pfx)。 密碼資訊會儲存在您的個人金鑰容器清單和您的個人憑證存放區中。

[建立測試憑證] 按鈕

可讓您建立憑證來進行測試。 測試憑證用來簽署 ClickOnce 應用程式和部署資訊清單。

按一下 [建立測試憑證] 會開啟 [建立測試憑證] 對話方塊，您可在其中輸入測試憑證之強式名稱金鑰檔的密碼。 這個檔案的名稱為 <專案名稱>_TemporaryKey.pfx。 如果您按一下 [確定]，而未輸入密碼，則 .pfx 檔案未使用密碼進行加密。

[時間戳記伺服器 URL] 方塊

指定將簽章加上時間戳記之伺服器的位址。 當您提供憑證時，這個外部網站會驗證應用程式的簽署時間。

## <a name="assembly-signing"></a>組件簽署

[簽署組件] 核取方塊

選取這個核取方塊可簽署組件並建立強式名稱金鑰檔。 如需使用 [專案設計工具] 簽署組件的詳細資訊，請參閱[如何：簽署組件 (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)。

此選項使用由 Windows 軟體開發套件 (SDK) 提供的 Al.exe 工具來簽署組件。 如需 Al.exe 的詳細資訊，請參閱[如何：使用強式名稱簽署組件](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)。

[選擇強式名稱金鑰檔] 清單

可讓您指定用來簽署組件的新或現有強式名稱金鑰檔。 選取 **\<Browse...>** 以選取現有的金鑰檔。

選取 **\<New...>** 即可建立用來簽署元件的新金鑰檔。 [建立強式名稱金鑰] 對話方塊隨即出現，可用來指定金鑰檔名稱並使用密碼來保護金鑰檔。 密碼長度至少必須是 6 個字元。 如果您指定密碼，則會建立個人資訊交換 (.pfx) 檔案；如果您未指定密碼，則會建立強式名稱金鑰 (.snk) 檔案。

[變更密碼] 按鈕

變更用來簽署組件之個人資訊交換 (.pfx) 金鑰檔的密碼。

按一下 [變更密碼] 會開啟 [變更金鑰密碼] 對話方塊。 在這個對話方塊中，[舊密碼] 是金鑰檔的目前密碼。 [新密碼] 長度至少必須是 6 個字元。 密碼資訊會儲存在目前使用者的 Windows 憑證存放區中。

[僅延遲簽署] 核取方塊

選取這個核取方塊可啟用延遲簽署。

請注意，延遲簽署專案將無法執行，也無法進行偵錯。 不過，您可以搭配使用 [Sn.exe (強式名稱工具)](/dotnet/framework/tools/sn-exe-strong-name-tool) 與 `-Vr` 選項，以在開發期間略過驗證。

> [!NOTE]
> 當您簽署組件時，不一定可以存取私密金鑰。 例如，組織可能會有嚴密保護的金鑰組，即使開發人員也沒有這類金鑰組的日常存取權。 公開金鑰可能可以使用，但只有少數人才能存取私密金鑰。 在這類情況下，您可以使用「延遲」或「部分簽署」提供公開金鑰，並將私密金鑰的新增延遲到交付組件時。

## <a name="see-also"></a>另請參閱

- [專案屬性參考](../../ide/reference/project-properties-reference.md)
- [管理元件和資訊清單簽署](../../ide/managing-assembly-and-manifest-signing.md)
- [如何：簽署應用程式和部署資訊清單](../../ide/how-to-sign-application-and-deployment-manifests.md)
- [如何：簽署組件 (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)
- [如何：使用強式名稱簽署組件](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [強式名稱的元件](/dotnet/framework/app-domains/strong-named-assemblies)
