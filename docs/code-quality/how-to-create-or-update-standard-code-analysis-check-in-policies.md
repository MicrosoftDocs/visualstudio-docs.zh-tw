---
title: 建立或更新標準程式碼分析簽入原則
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d034d65cd356ff44a42d10840ae064d81713457f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587533"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>如何：建立或更新標準程式碼分析簽入原則

您可以使用程式碼分析簽入原則，要求在 Azure DevOps 專案中的所有程式碼專案上執行程式碼分析。 需要程式碼分析可以改善已簽入程式碼基底之程式碼的品質。

> [!NOTE]
> 只有當您使用 Team Foundation Server 時，才可使用這項功能。

程式碼分析簽入原則會在專案設定中設定，並套用至每個程式碼專案。 程式碼分析回合是針對程式碼專案的專案（. .xxproj）檔案中的程式碼專案所設定。 程式碼分析回合會在本機電腦上執行。 當您啟用程式碼分析簽入原則時，要簽入之程式碼專案中的檔案必須在其上次編輯後編譯，且包含的程式碼分析執行至少必須在變更的電腦上執行專案設定中的規則。已進行。

- 針對 managed 程式碼，您可以藉由指定包含程式碼分析規則子集的*規則集*來設定簽入原則。

- 針對 C/C++程式碼，在 Visual Studio 2017 15.6 版和更早版本中，簽入原則會要求執行所有程式碼分析規則。 您可以新增預處理器指示詞，以停用 Azure DevOps 專案中個別程式碼專案的特定規則。 在15.7 和更新版本中，您可以使用 **/analyze：規則集**來指定要執行的規則。 如需詳細資訊，請參閱[使用規則集指定C++要執行的規則](using-rule-sets-to-specify-the-cpp-rules-to-run.md)。

在您指定 managed 程式碼的簽入原則之後，小組成員可以將程式碼專案的程式碼分析設定同步處理到 Azure DevOps 專案原則設定。

## <a name="to-open-the-check-in-policy-editor"></a>若要開啟簽入原則編輯器

1. 在 Team Explorer 中，以滑鼠右鍵按一下專案名稱，指向 [**專案設定**]，然後按一下 [**原始檔控制**]。

1. 在 [**原始檔控制**] 對話方塊中，選取 [**簽入原則**] 索引標籤。

1. 請執行下列其中一項動作：

    - 按一下 **[新增]** 以建立新的簽入原則。

    - 按兩下 [**原則類型**] 清單中現有的程式**代碼分析**專案，以變更原則。

## <a name="to-set-policy-options"></a>若要設定原則選項

選取或清除下列選項：

|選項|描述|
|------------|-----------------|
|**強制簽入僅包含屬於目前方案的檔案。**|程式碼分析只能在方案和專案設定檔中指定的檔案上執行。 此原則可保證會分析屬於方案一部分的所有程式碼。|
|**強制執行 CC++ /程式碼分析（/analyze）**|需要使用/analyze 編譯器選項C++來建立所有 C 或專案，以在可以簽入之前執行程式碼分析。|
|**針對受控碼強制執行程式碼分析**|要求所有 managed 專案必須先執行程式碼分析和組建，才能將它們簽入。|

## <a name="to-specify-a-managed-rule-set"></a>若要指定受管理的規則集

從 [**執行此規則集**] 清單中，使用下列其中一種方法：

- 選取 [Microsoft 標準規則集]。

- 按一下 [ **\<從原始檔控制選取規則集]，選取自訂規則集 .。。>** 。 然後，在原始檔控制瀏覽器中輸入規則集的版本控制路徑。 版本控制路徑的語法為：

   **$/** `TeamProjectName` **/** `VersionControlPath`

如需如何建立和執行自訂簽入原則規則集的詳細資訊，請參閱[針對 Managed 程式碼執行自訂簽入](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)原則。

## <a name="see-also"></a>請參閱

- [為受控碼實作自訂程式碼分析簽入原則](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)
