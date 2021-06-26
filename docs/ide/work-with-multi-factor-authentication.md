---
title: 使用需要多重要素驗證的帳戶
ms.date: 05/27/2020
ms.custom: SEO-VS-2020
ms.topic: conceptual
description: 瞭解如何搭配使用 Visual Studio 與需要多重要素驗證的帳戶。
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9ac42ccff8c7bffcc22c453002aad1caf6935d28
ms.sourcegitcommit: e4630a3bb89b4d606fe2cbd709bc773c5b538b78
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2021
ms.locfileid: "112975679"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>如何搭配需要多重要素驗證的帳戶使用 Visual Studio

與外部來賓使用者共同作業時，最好是使用條件式存取來保護您的應用程式和資料 **(CA)** 原則，例如 **(MFA) 的多重要素驗證**。  

啟用之後，來賓使用者將不只需要使用者名稱和密碼即可存取您的資源，且必須滿足額外的安全性需求。 MFA 原則可以在租用戶、應用程式或個別來賓使用者層級強制執行，方式就像針對您自己組織的成員啟用這些原則一樣。 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>MFA 原則會如何影響 Visual Studio 體驗？
在16.6 之前的 Visual Studio 版本，與已啟用 CA 原則（例如 MFA）的帳戶搭配使用，並與兩個或多個租使用者相關聯時，可能會有降級的驗證體驗。

這些問題可能會導致您的 Visual Studio 實例每日提示重新進行多次驗證。 您可能必須重新輸入先前已驗證租使用者的認證，即使在相同的 Visual Studio 會話期間也是如此。

## <a name="using-visual-studio-with-mfa-policies"></a>搭配使用 Visual Studio 與 MFA 原則
在16.6 版中，我們新增了 Visual Studio 2019 的新功能，可簡化使用者存取透過 CA 原則（例如 MFA）保護之資源的方式。 若要使用這個增強的工作流程，您必須選擇使用系統的預設網頁瀏覽器，作為新增和重新驗證 Visual Studio 帳戶的機制。  

> [!WARNING]
> 若未使用此工作流程，可能會觸發降級的體驗，而導致在新增或重新驗證入時 Visual Studio 帳戶時，產生多個額外的驗證提示。 

### <a name="enabling-system-web-browser"></a>啟用系統網頁瀏覽器

> [!NOTE] 
> 為了獲得最佳體驗，我們建議您先清除系統的預設網頁瀏覽器資料，再繼續進行此工作流程。 此外，如果您在 [ **存取公司或學校**] 下的 Windows 10 設定中有工作或學校帳戶，請確認這些帳戶是否經過適當的驗證。

若要啟用此工作流程，請移至 Visual Studio 的 [選項] 對話方塊 **(工具 > 選項 ... )**，選取 [**帳戶**] 索引標籤，然後在 [**使用下列方式新增和** 重新驗證帳戶] 下拉式清單中選取 [**系統網頁瀏覽器** 

:::image type="content" source="media/select-system-web-browser.png" alt-text="從功能表選取 [系統網頁瀏覽器]。":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>使用 MFA 原則登入其他帳戶 
啟用系統網頁瀏覽器工作流程之後，您可以透過 [帳戶設定] 對話方塊 **(檔 > 帳戶設定 ... )**，以平常的方式登入或新增帳戶以 Visual Studio。   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="將新的個人化帳戶新增至 Visual Studio。" border="false":::

此動作會開啟您系統的預設網頁瀏覽器、要求您登入您的帳戶，並驗證任何必要的 MFA 原則。

在登入程式期間，您可能會收到額外的提示，要求您保持登入狀態。 此提示可能會在第二次使用帳戶登入時顯示。 若要將重新輸入認證的需求降到最低，建議您選取 **[是]**，因為這樣可確保您的認證會在瀏覽器會話中保留。

:::image type="content" source="media/kmsi.png" alt-text="要保持登入嗎？":::

根據您的開發活動和資源設定，您可能仍會在會話期間提示您重新輸入認證。 當您新增資源，或嘗試存取資源，但未事先符合其 CA/MFA 授權需求時，就會發生這種情況。

## <a name="reauthenticating-an-account"></a>重新驗證入時帳戶  
如果您的帳戶發生問題，Visual Studio 可能會要求您重新輸入您的帳號憑證。  

:::image type="content" source="media/reauthenticate-account.png" alt-text="重新驗證您的 Visual Studio 帳戶。":::

按一下 [ **重新輸入您的認證** ] 將會開啟系統的預設網頁瀏覽器，並嘗試自動重新整理您的認證。 如果不成功，系統會要求您登入您的帳戶，並驗證任何必要的 CA/MFA 原則。

> [!NOTE] 
> 為了獲得最佳體驗，請讓您的瀏覽器保持開啟，直到您的資源驗證所有 CA/MFA 原則為止。 關閉瀏覽器可能會導致先前建立的 MFA 狀態遺失，並可能提示其他授權提示。

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>如何選擇不要在 Visual Studio 中使用特定的 Azure Active Directory 租使用者

Visual Studio 2019 16.6 版提供個別或全域篩選出租使用者的彈性，可有效地從 Visual Studio hidding 它們。 篩選不需要向該租使用者進行驗證，但這也表示您將無法存取任何相關聯的資源。

當您有多個租使用者，但想要將目標設為特定子集來優化開發環境時，這項功能會很有用。 當您無法驗證特定 CA/MFA 原則時，它也可以協助實例，因為您可以篩選出違規的租使用者。 

### <a name="how-to-filter-out-all-tenants"></a>如何篩選出所有租使用者
若要全域篩選所有租使用者，請開啟 [帳戶設定] 對話方塊， **(檔案 > 帳戶設定 ... )** 並取消選取 [ **跨所有 Azure Active directory 進行驗證** ] 核取方塊。

取消選擇該選項可確保您只會使用帳戶的預設租使用者進行驗證。 這也表示您將無法存取任何與其他租使用者相關聯的資源。您的帳戶可能是來賓帳戶。

### <a name="how-to-filter-out-individual-tenants"></a>如何篩選掉個別租使用者
若要篩選與您的 Visual Studio 帳戶相關聯的租使用者，請開啟 [帳戶設定] 對話方塊， ([檔案 **> 帳戶設定 ...] )** 然後按一下 [套用 **篩選**]。 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="套用篩選。" border="false":::

[ **篩選帳戶** ] 對話方塊隨即出現，可讓您選取要與您的帳戶搭配使用的租使用者。 

:::image type="content" source="media/select-filter-account.png" alt-text="選取要篩選的帳戶。":::

## <a name="see-also"></a>另請參閱

- [登入 Visual Studio](signing-in-to-visual-studio.md)
- [登入 Visual Studio for Mac](/visualstudio/mac/signing-in)
- [Work with multiple user accounts](work-with-multiple-user-accounts.md)
