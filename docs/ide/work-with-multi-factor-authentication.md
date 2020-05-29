---
title: 使用需要多重要素驗證的帳戶
ms.date: 05/27/2020
ms.topic: conceptual
description: 瞭解如何使用 Visual Studio 搭配需要多重要素驗證的帳戶。
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 696664aa5aa92a3e9a675df4803a3e65e3e81f36
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84185613"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>如何使用 Visual Studio 搭配需要多重要素驗證的帳戶

與外部來賓使用者共同作業時，使用**條件式存取（CA）** 原則（例如**多重要素驗證（MFA））** 來保護您的應用程式和資料是個不錯的主意。  

啟用之後，來賓使用者只需要使用者名稱和密碼就能存取您的資源，而且必須滿足額外的安全性需求。 MFA 原則可以在租用戶、應用程式或個別來賓使用者層級強制執行，方式就像針對您自己組織的成員啟用這些原則一樣。 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>MFA 原則會影響 Visual Studio 體驗嗎？
16.6 之前的 Visual Studio 版本在與已啟用 CA 原則（例如 MFA）的帳戶搭配使用時，可能會有降級的驗證體驗，而且會與兩個或多個租使用者相關聯。

這些問題可能會導致您的 Visual Studio 實例每日多次重新驗證一次。 您可能必須重新輸入先前已驗證租使用者的認證，即使在相同的 Visual Studio 會話期間也一樣。

## <a name="using-visual-studio-with-mfa-policies"></a>搭配使用 Visual Studio 與 MFA 原則
在16.6 版本中，我們新增了 Visual Studio 2019 的新功能，可簡化使用者存取透過 CA 原則（例如 MFA）保護之資源的方式。 若要使用這個增強的工作流程，您必須選擇使用系統的預設網頁瀏覽器，做為新增和重新驗證 Visual Studio 帳戶的機制。  

> [!WARNING]
> 不使用此工作流程可能會觸發降級的體驗，而在新增或重新驗證入時 Visual Studio 帳戶時，會產生多個額外的驗證提示。 

### <a name="enabling-system-web-browser"></a>啟用系統網頁瀏覽器  
若要啟用此工作流程，請移至 Visual Studio 的 [選項] 對話方塊 **（[工具] [> 選項 ...]）**，選取 [**帳戶**] 索引標籤，然後選取 [**新增並**重新驗證帳戶] 底下的 [**系統網頁瀏覽器**] 

:::image type="content" source="media/select-system-web-browser.png" alt-text="從功能表中選取 [系統網頁瀏覽器]。":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>使用 MFA 原則登入其他帳戶 
啟用系統網頁瀏覽器工作流程之後，您可以透過 [帳戶設定] 對話方塊（[檔案 **> 帳戶設定 ...]）**，以平常的方式登入或新增帳戶到 Visual Studio。   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="將新的個人化帳戶新增至 Visual Studio。" border="false":::

此動作會開啟您系統的預設網頁瀏覽器，要求您登入您的帳戶，並驗證任何必要的 MFA 原則。 

> [!NOTE] 
> 透過整個程式讓瀏覽器保持開啟狀態，以獲得最佳體驗，因為關閉瀏覽器可能會觸發額外的授權提示。 

## <a name="reauthenticating-an-account"></a>重新驗證入時帳戶  
如果您的帳戶發生問題，Visual Studio 可能會要求您重新輸入您的帳號憑證。  

:::image type="content" source="media/reauthenticate-account.png" alt-text="重新驗證您的 Visual Studio 帳戶。":::

按一下 [**重新輸入您的認證**] 將會開啟系統的預設網頁瀏覽器，並嘗試自動重新整理您的認證。 如果不成功，系統會要求您登入您的帳戶，並驗證任何必要的 MFA 原則。 

> [!NOTE] 
> 透過整個程式讓瀏覽器保持開啟狀態，以獲得最佳體驗，因為關閉瀏覽器可能會觸發額外的授權提示。 

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>如何選擇不在 Visual Studio 中使用特定的 Azure Active Directory 租使用者

Visual Studio 2019 16.6 版提供篩選特定租使用者的彈性，這會將它們從 Visual Studio 中隱藏。 篩選不需要向該租使用者進行驗證，但這也表示您將無法存取任何相關聯的資源。 

當您有多個租使用者，但想要將目標設為特定子集，以優化您的開發環境時，這項功能就很有用。 當您無法驗證特定的 CA/MFA 原則時，它也可以在實例中協助，因為您可以篩選出有問題的租使用者。 

### <a name="how-to-filter-out-a-tenant"></a>如何篩選出租使用者
若要篩選與 Visual Studio 帳戶相關聯的租使用者，請開啟 [帳戶設定] 對話方塊（[檔案 **> 帳戶設定 ...]）** ，然後按一下 [套用**篩選**]。 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="套用篩選準則。" border="false":::

[**篩選帳戶**] 對話方塊隨即出現，可讓您選取要與您的帳戶搭配使用的租使用者。 

:::image type="content" source="media/select-filter-account.png" alt-text="選取要篩選的帳戶。":::

## <a name="see-also"></a>另請參閱

- [登入 Visual Studio](signing-in-to-visual-studio.md)
- [登入 Visual Studio for Mac](/visualstudio/mac/signing-in)
- [Work with multiple user accounts](work-with-multiple-user-accounts.md)