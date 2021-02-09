---
title: 受控碼的自訂程式碼分析簽入原則
ms.date: 11/04/2016
description: 瞭解如何建立自訂的程式碼分析簽入原則。 瞭解如何確保 Visual Studio 的 managed 程式碼符合 Azure DevOps 專案原則。
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 8e682c3d3312be5c4f4639fc2642a398e321fc78
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859875"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>為受控碼實作自訂程式碼分析簽入原則

程式碼分析簽入原則會指定一組規則，Azure DevOps 專案的成員必須在原始程式碼中執行，才能將其簽入版本控制。 Microsoft 提供一組標準 *規則集* ，將程式碼分析規則分組至功能區域。 *自訂簽入原則規則集會* 指定專案特定的一組程式碼分析規則。 規則集會儲存在一個規則集檔案中。

簽入原則是在 Azure DevOps 專案層級設定，並由版本控制樹狀結構中的規則集檔案的位置指定。 Team policy 自訂規則集的版本控制位置沒有任何限制。

在每個專案的 [屬性] 視窗中，針對個別程式碼專案設定程式碼分析。 程式碼專案的自訂規則集是由本機電腦上的規則集檔案的實體位置所指定。 指定與程式碼專案位於相同磁片磁碟機的. 規則集檔案時，Visual Studio 會使用專案設定中檔案的相對路徑。

建立 Azure DevOps 專案自訂規則集的建議作法是在不屬於任何程式碼專案的特殊資料夾中儲存簽入原則。規則集檔案。 如果您將檔案儲存在專用的資料夾中，您可以套用限制可以編輯規則檔案的許可權，而且您可以輕鬆地將包含專案的目錄結構移至另一個目錄或電腦。

## <a name="create-the-project-custom-check-in-rule-set"></a>建立專案自訂簽入規則集

若要建立 Azure DevOps 專案的自訂規則集，您必須先針對 **原始檔控制總管** 中的簽入原則規則集建立特殊資料夾。 然後，您可以建立規則集檔案，然後將檔案加入至版本控制。 最後，您會將規則集指定為專案的程式碼分析簽入原則。

> [!NOTE]
> 若要在 Azure DevOps 專案中建立資料夾，您必須先將專案根目錄對應至本機電腦上的位置。

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>建立簽入原則規則集的版本控制資料夾

1. 在 Team Explorer 中，展開專案節點，然後按一下 [ **原始檔控制**]。

2. 在 [ **資料夾** ] 窗格中，以滑鼠右鍵按一下專案，然後按一下 [ **新增資料夾**]。

3. 在 [主要原始檔控制] 窗格中，以滑鼠右鍵按一下 [ **新增資料夾**]，然後按一下 [ **重新命名**]，然後輸入規則集資料夾的名稱。

### <a name="to-create-the-check-in-policy-rule-set"></a>若要建立簽入原則規則集

1. 在 [ **檔案** ] 功能表上，指向 [ **新增**]，然後按一下 [ **檔案**]。

2. 在 [ **類別** ] 清單中，按一下 **[一般**]。

3. 在 [ **範本** ] 清單中，按兩下 [程式 **代碼分析規則集**]。

4. [指定](../code-quality/how-to-create-a-custom-rule-set.md) 要包含在規則集中的規則，然後將規則集檔案儲存至您所建立的規則集資料夾。

### <a name="to-add-the-rule-set-file-to-version-control"></a>將規則集檔案新增至版本控制

1. 在 **原始檔控制總管** 中，以滑鼠右鍵按一下新資料夾，然後按一下 [ **將專案加入資料夾**]。

     如需詳細資訊，請參閱 [Git 和 Azure Repos](/azure/devops/repos/git/overview?view=vsts&preserve-view=true)。

2. 按一下您建立的規則集檔案，然後按一下 **[完成]**。

     檔案會新增至原始檔控制，並簽出給您。

3. 在 [ **原始檔控制總管** 詳細資料] 視窗中，以滑鼠右鍵按一下檔案名，然後按一下 [ **簽入暫** 止的變更]。

4. 在 [ **簽入** ] 對話方塊中，您可以選擇新增批註，然後按一下 [ **簽入**]。

    > [!NOTE]
    > 如果您已針對 Azure DevOps 專案設定程式碼分析簽入原則，而且您已選取 [ **強制簽入] 只包含屬於目前方案** 的檔案，您將會觸發原則失敗警告。 在 [原則失敗] 對話方塊中，選取 [覆 **寫原則失敗並繼續簽入**]。 新增必要的批註，然後按一下 **[確定]**。

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>將規則集檔案指定為簽入原則

1. 在 [ **小組** ] 功能表上，指向 [ **專案設定**]，然後按一下 [ **原始檔控制**]。

2. 按一下 [ **簽入原則**]，然後按一下 [ **新增**]。

3. 在 [ **簽入原則** ] 清單中，按兩下 [程式 **代碼分析**]，並確定已選取 [ **強制執行 Managed 程式碼分析** ] 核取方塊。

4. 在 [ **執行此規則集** ] 清單中，按一下 **\<Select Rule Set from Source Control>** 。

5. 在 [版本控制] 中輸入簽入原則規則集檔案的路徑。

     路徑必須符合下列語法：

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > 您可以在 **原始檔控制總管** 中使用下列其中一個程式來複製路徑：

    - 在 [ **資料夾** ] 窗格中，按一下包含規則集檔案的資料夾。 複製 [ **來源** ] 方塊中出現之資料夾的版本控制路徑，並手動輸入規則集檔案的名稱。

    - 在 [詳細資料] 視窗中，以滑鼠右鍵按一下規則集檔案，然後按一下 [ **屬性**]。 在 [ **一般** ] 索引標籤上，複製 [ **伺服器名稱**] 中的值。

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>將程式碼專案同步處理至簽入原則規則集

您可以在程式碼專案的 [屬性] 對話方塊中，將專案簽入原則規則集指定為程式碼專案設定的程式碼分析規則集。 如果規則集與程式碼專案位於相同的磁片磁碟機上，則在從 [檔案] 對話方塊中選取路徑時，會使用相對路徑來指定規則集。 相對路徑可將專案屬性設定移植到使用類似本機版本控制結構的其他電腦。

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>將專案規則集指定為程式碼專案的規則集

1. 如有必要，請從版本控制中取出簽入原則規則集資料夾和檔案。

   您可以在 **原始檔控制總管** 中執行此步驟，方法是在 [規則集] 資料夾上按一下滑鼠右鍵，然後按一下 [ **取得最新的版本**]。

2. 在 **方案總管** 中，以滑鼠右鍵按一下程式碼專案，然後按一下 [ **屬性**]。

3. **按一下 [程式碼分析**]。

4. 如有必要，請在 [設定] 和 [**平臺**] 清單中按一下 **適當的選項**。

::: moniker range="vs-2017"

5. 若要在每次使用指定的設定建立程式碼專案時執行程式碼分析，請選取 [ **在組建時啟用程式碼分析**]。

::: moniker-end

::: moniker range=">=vs-2019"

5. 若要在每次使用指定的設定建立程式碼專案時執行程式碼分析，請選取 [**二進位分析器**] 區段中的 [**在組建上執行**]。

::: moniker-end

6. 在 [ **執行此規則集** ] 清單中，按一下 **\<Browse>** 。

8. 選取 [簽入原則] 規則集檔案的本機版本。
