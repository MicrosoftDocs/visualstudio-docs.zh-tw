---
title: 針對 Managed 程式碼執行自訂程式碼分析簽入原則 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1cf759e01e5f152f2220124c90f145bfbbe3c01d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651579"
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>為 Managed 程式碼實作自訂程式碼分析簽入原則
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

程式碼分析簽入原則會指定小組專案的成員必須在原始程式碼上執行的一組規則，才能簽入版本控制。 Microsoft 提供一組標準*規則集*，將程式碼分析規則分組到功能區域中。 *自訂簽入原則規則集會*指定 team 專案專屬的一組程式碼分析規則。 規則集會儲存在. 規則集檔案中。

 簽入原則是在 team 專案層級設定，並由版本控制樹狀結構中的規則集檔案的位置指定。 小組原則自訂規則集的版本控制位置沒有任何限制。

 程式碼分析會針對每個專案的 [屬性] 視窗中的個別程式碼專案進行設定。 程式碼專案的自訂規則集是由本機電腦上的規則集檔案的實體位置所指定。 當指定的規則集檔案與程式碼專案位於相同的磁片磁碟機時，Visual Studio 會在專案設定中使用該檔案的相對路徑。

 建立 team 專案自訂規則集的建議做法是在不屬於任何程式碼專案的特殊資料夾中儲存簽入原則。規則集檔案。 如果您將檔案儲存在專用的資料夾中，您可以套用限制誰可以編輯規則檔的許可權，而且您可以輕鬆地將包含該專案的目錄結構移到另一個目錄或電腦。

## <a name="creating-the-team-project-custom-check-in-rule-set"></a>建立 Team 專案自訂簽入規則集
 若要為 team 專案建立自訂規則集，您必須先在**原始檔控制總管**中建立簽入原則規則集的特殊資料夾。 接著，您會建立規則集檔案，並將檔案加入至版本控制。 最後，您可以將規則集指定為 team 專案的程式碼分析簽入原則。

> [!NOTE]
> 若要在 team 專案中建立資料夾，您必須先將 team 專案根目錄對應至本機電腦上的位置。 如需詳細資訊，請參閱[建立和使用工作區（舊）](https://msdn.microsoft.com/db4d5692-179a-44fe-ad31-0c1c900c9cb2)。

#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>建立簽入原則規則集的版本控制資料夾

1. 在 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 中，展開 [team 專案] 節點，然後按一下 [**原始檔控制**]。

2. 在 [**資料夾**] 窗格中，以滑鼠右鍵按一下 team 專案，然後按一下 [**新增資料夾**]。

3. 在主要 [原始檔控制] 窗格中，以滑鼠右鍵按一下 [**新增資料夾**]，按一下 [**重新命名**]，然後輸入規則集資料夾的名稱。

#### <a name="to-create-the-check-in-policy-rule-set"></a>若要建立簽入原則規則集

1. **在 [檔案**] 功能表上，指向 [**新增**]，**然後按一下 [** 檔案]。

2. 在 [**類別**] 清單中，按一下 **[一般**]。

3. 在 [**範本**] 清單中，按兩下 [程式**代碼分析規則集**]。

4. 指定要包含在規則集中的規則，然後將規則集檔案儲存到您所建立的規則集資料夾中。

     如需詳細資訊，請參閱[建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)

#### <a name="to-add-the-rule-set-file-to-version-control"></a>若要將規則集檔案加入至版本控制

1. 在**原始檔控制總管**中，以滑鼠右鍵按一下新的資料夾，然後按一下 [**將專案加入資料夾**]。

     如需詳細資訊，請參閱[使用版本控制](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314)。

2. 按一下您所建立的規則集檔案，然後按一下 **[完成]** 。

     檔案會加入至原始檔控制，並簽出給您。

3. 在 [**原始檔控制總管**詳細資料] 視窗中，以滑鼠右鍵按一下檔案名，然後按一下 [**簽入暫**止的變更]。

4. 在 [**簽入**] 對話方塊中，您可以選擇新增批註，然後按一下 [**簽入**]。

    > [!NOTE]
    > 如果您已經為您的 team 專案設定程式碼分析簽入原則，而且已選取 [**強制簽入僅包含屬於目前方案**的檔案]，則會觸發原則失敗警告。 在 [原則失敗] 對話方塊中，選取 [覆**寫原則失敗並繼續簽入**]。 新增必要的批註，然後按一下 **[確定]** 。

#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>將規則集檔案指定為簽入原則

1. 在 [**小組**] 功能表上，指向 [ **team 專案設定**]，然後按一下 [**原始檔控制**]。

2. 按一下 [**簽入原則**]，然後按一下 [**新增**]。

3. 在 [**簽入原則**] 清單中，按兩下 [程式**代碼分析**]，並確定已選取 [**針對 Managed 程式碼強制執行程式碼分析**] 核取方塊。

4. 在 [**執行此規則集**] 清單中，按一下 [**從原始檔控制 \<Select 規則集] >** 。

5. 在 [版本控制] 中，輸入簽入原則規則集檔案的路徑。

     路徑必須符合下列語法：

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > 您可以使用**原始檔控制總管**中的下列其中一個程式來複製路徑：

    - 在 [**資料夾**] 窗格中，按一下包含規則集檔案的資料夾。 複製出現在 [**來源**] 方塊中之資料夾的版本控制路徑，並手動輸入規則集檔案的名稱。

    - 在 [詳細資料] 視窗中，在規則集檔案上按一下滑鼠右鍵，然後按一下 [**屬性**]。 在 [**一般**] 索引標籤上，複製 [**伺服器名稱**] 中的值。

## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>將程式碼專案同步處理到簽入原則規則集
 在程式碼專案的 [屬性] 對話方塊中，您可以將 team 專案簽入原則規則集指定為程式碼專案設定的程式碼分析規則集。 如果規則集位於與程式碼專案相同的磁片磁碟機上，當從 [檔案] 對話方塊中選取路徑時，會使用相對路徑來指定規則集。 相對路徑可讓專案屬性設定可移植到其他使用類似本機版本控制結構的電腦。

#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>若要將 team 專案規則集指定為程式碼專案的規則集

1. 如有需要，請從版本控制中取出簽入原則規則集資料夾和檔案。

     您可以在**原始檔控制總管**中執行此步驟，方法是在 [規則集] 資料夾上按一下滑鼠右鍵，然後按一下 [**取得最新的版本**]。

2. 在**方案總管**中，以滑鼠右鍵按一下程式碼專案，然後按一下 [**屬性**]。

3. **按一下 [程式碼分析**]。

4. 如有需要，請在 [設定] 和 [**平臺**] 清單中按一下**適當的選項**。

5. 若要在每次使用指定的設定來建立程式碼專案時執行程式碼分析，請選取 [**在組建上啟用程式碼分析（定義 CODE_ANALYSIS 常數）** ] 核取方塊。

6. 若要忽略其他公司元件中的程式碼，請選取 [**隱藏產生的程式碼的結果**] 核取方塊。

7. 在 **執行此規則集** 清單中，按一下  **\<Browse .。。>** 。

8. 指定簽入原則規則集檔案的本機版本。
