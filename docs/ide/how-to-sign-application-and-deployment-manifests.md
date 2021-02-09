---
title: 如何：簽署應用程式和部署資訊清單
description: 瞭解簽署發行 ClickOnce 應用程式和部署資訊清單的需求。 對於 .exe 架構的應用程式，簽署是選擇性的。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5568961cc8b527ecd724ab9a1d26ab4a641696b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869280"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>如何：簽署應用程式和部署資訊清單

如果您想要使用 ClickOnce 部署來發行應用程式，必須搭配使用 Authenticode 技術和公開/私密金鑰組來簽署應用程式和部署資訊清單。 您可以使用 Windows 憑證存放區或金鑰檔的憑證來簽署資訊清單。

如需詳細資訊，請參閱 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)。

針對 *.exe* 應用程式，您可以選擇是否要簽署 ClickOnce 資訊清單。 如需詳細資訊，請參閱本文件的＜產生未簽署的資訊清單＞ 一節。

如需建立金鑰檔的資訊，請參閱[如何：建立公用/私密金鑰組](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)。

> [!NOTE]
> Visual Studio 只支援副檔名為 *.pfx* 的個人資訊交換 (PFX) 金鑰檔。 不過，您可以在專案屬性的 [簽署] 頁面中，按一下 [從存放區選取]，即可從目前使用者的 Windows 憑證存放區選取其他類型的憑證。

## <a name="sign-using-a-certificate"></a>使用憑證簽署

1. 請移至專案屬性視窗 (以滑鼠右鍵按一下 [方案總管] 中的專案節點，然後選取 [屬性])。 在 [簽署] 索引標籤上，選取 [簽署 ClickOnce 資訊清單] 核取方塊。

2. 按一下 [從存放區選取] 按鈕。

     [選取憑證] 對話方塊隨即出現，並顯示 Windows 憑證存放區的內容。

    > [!TIP]
    > 如果您按一下 [按一下這裡檢視憑證屬性]，則會顯示 [憑證詳細資料] 對話方塊。 這個對話方塊包含憑證的詳細資訊與其他選項。 按一下 [憑證] 以檢視其他說明資訊。

3. 選取您想要用來簽署資訊清單的憑證。

4. 此外，您可以在 [時間戳記伺服器 URL] 文字方塊中，指定時間戳記伺服器的位址。 這種伺服器可提供時間戳記，以指定資訊清單的簽署時間。

## <a name="sign-using-an-existing-key-file"></a>使用現有金鑰檔案簽署

1. 在 [簽署] 頁面上，選取 [簽署 ClickOnce 資訊清單] 核取方塊。

2. 按一下 [從檔案選取] 按鈕。

     [選取檔案] 對話方塊隨即出現。

3. 在 [選取檔案] 對話方塊中，瀏覽至您要使用的金鑰檔 (*.pfx*) 位置，然後按一下 [開啟]。

    > [!NOTE]
    > 此選項僅支援具有 *.pfx* 副檔名的檔案。 如果您的金鑰檔或憑證是其他格式，請將它儲存在 Windows 憑證存放區，並遵循上一個程序所述選取該憑證。 選取的憑證用途應包含程式碼簽署。

     [輸入密碼以開啟檔案] 對話方塊隨即出現。 (如果 *.pfx* 檔案是儲存在您的 Windows 憑證存放區，或未受密碼保護，系統就不會提示您輸入密碼)。

4. 輸入密碼以存取金鑰檔，然後選取 **Enter**。

> [!NOTE]
> *.pfx* 檔案不能包含憑證鏈結資訊。 如果有的話，將會發生下列匯入錯誤：找 **不到憑證和私密金鑰進行解密**。 若要移除憑證鏈資訊，您可以使用 *certmgr.msc* ，並停用在匯出 * .pfx 檔案時 **包含所有憑證**[的選項](/previous-versions/aa730868(v=vs.80))。

## <a name="sign-using-a-test-certificate"></a>使用測試憑證簽署

1. 在 [簽署] 頁面上，選取 [簽署 ClickOnce 資訊清單] 核取方塊。

2. 若要建立新憑證以進行測試，請按一下 [建立測試憑證] 按鈕。

3. 在 [建立測試憑證] 對話方塊中，輸入密碼，以協助保護您的測試憑證。

## <a name="generate-unsigned-manifests"></a>產生未簽署的資訊清單

針對 *.exe* 應用程式，您可以選擇是否要簽署 ClickOnce 資訊清單。 下列程序說明如何產生未簽署的 ClickOnce 資訊清單。

> [!IMPORTANT]
> 未簽署的資訊清單可以簡化應用程式的開發和測試作業。 不過，未簽署的資訊清單會在生產環境中帶來很大的安全性風險。 因此，只有當您是在內部網路 (其與網際網路或其他來源的惡意程式碼完全隔離) 的電腦上執行 ClickOnce 應用程式時，才建議使用未簽署的資訊清單。

除非已產生的雜湊中特別排除一或多個檔案，否則 ClickOnce 預設會自動簽署資訊清單。 換句話說，如果所有檔案都包含在雜湊中，發行應用程式時即會產生已簽署的資訊清單，即使清除 [簽署 ClickOnce 資訊清單] 核取方塊亦同。

### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>產生未簽署的資訊清單，並在產生的雜湊中包含所有檔案

1. 若要產生未簽署的資訊清單，以在產生的雜湊中包含所有檔案，您必須先發行應用程式與已簽署的資訊清單。 因此，請遵循先前程序的其中之一，先簽署 ClickOnce 資訊清單，然後再發行應用程式。

2. 在 [簽署] 頁面上，清除 [簽署 ClickOnce 資訊清單] 核取方塊。

3. 重設發行版本，僅讓一個版本的應用程式可供使用。 根據預設，每當您發行應用程式時，Visual Studio 就會自動遞增發行版本的修訂編號。 如需詳細資訊，請參閱[如何：設定 ClickOnce 發行版本](../deployment/how-to-set-the-clickonce-publish-version.md)。

4. 發行應用程式。

### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>產生未簽署的資訊清單，並從產生的雜湊中排除一或多個檔案

1. 在 [簽署] 頁面上，清除 [簽署 ClickOnce 資訊清單] 核取方塊。

2. 開啟 [應用程式檔案] 對話方塊，針對要從產生的雜湊中排除的檔案，將其 [雜湊] 設為 [排除]。

    > [!NOTE]
    > 從雜湊排除檔案時，會將 ClickOnce 設為停用自動簽署資訊清單，您即不需要先使用簽署的資訊清單來發行 (如先前程序所示)。

3. 發行應用程式。

## <a name="see-also"></a>另請參閱

- [強式名稱組件](/dotnet/framework/app-domains/strong-named-assemblies)
- [如何：建立公開/私密金鑰組](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)
- [專案設計工具、簽署頁](../ide/reference/signing-page-project-designer.md)
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
