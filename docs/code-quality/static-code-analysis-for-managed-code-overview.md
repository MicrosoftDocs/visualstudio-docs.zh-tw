---
title: 適用于 managed 程式碼的舊版分析
ms.date: 06/12/2019
description: 瞭解 Visual Studio 中的舊版分析。 瞭解如何隱藏警告，以及如何在簽入和組建期間手動、自動和執行分析。
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e8d9ddf88086772e0cd21bde856184954bc7143b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867681"
---
# <a name="overview-of-legacy-analysis-for-managed-code-in-visual-studio"></a>Visual Studio 中 managed 程式碼的舊版分析總覽

Visual Studio 可以用兩種方式執行 managed 程式碼的程式碼分析：使用 [舊版分析](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)，也稱為 managed 元件的 FxCop 靜態分析，以及更新式的 .NET Compiler Platform 型程式 [代碼分析器](../code-quality/roslyn-analyzers-overview.md)。 本主題涵蓋舊版分析。 若要深入瞭解以 .NET Compiler Platform 為基礎的程式碼分析，請參閱以 [.NET Compiler Platform 為基礎的分析器總覽](../code-quality/roslyn-analyzers-overview.md)。

Managed 程式碼的程式碼分析會分析 managed 元件，並報告元件的相關資訊，例如違反 [.Net 設計方針](/dotnet/standard/design-guidelines/)中所述的程式設計和設計規則。

分析工具會將分析期間所做的檢查顯示為警告訊息。 警告訊息會識別任何相關的程式設計和設計問題，並且在可能的時候，提供如何修正問題的資訊。

> [!NOTE]
> Visual Studio 中的 .NET Core 和 .NET Standard 專案不支援舊版分析 (靜態程式碼分析) 。 如果您在 .NET Core 或 .NET Standard 專案上執行程式碼分析做為 msbuild 的一部分，您會看到類似以下的錯誤 **： CA0055：無法識別的平臺 \<your.dll>**。 若要分析 .NET Core 或 .NET Standard 專案中的程式碼，請改為使用程式 [代碼分析器](../code-quality/roslyn-analyzers-overview.md) 。

## <a name="ide-integrated-development-environment-integration"></a>IDE (整合式開發環境) 整合

您可以手動或自動執行專案的程式碼分析。

若要在每次建立專案時執行程式碼分析，請選取專案的 [程式 **代碼分析** ] 屬性頁上的選項。 如需詳細資訊，請參閱 [如何：啟用和停用自動程式碼分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)。

若要在專案上手動執行程式碼分析，請從功能表列選擇 [**分析**  >  **執行程式碼分析**  >  **\<project> 執行** 程式碼分析]。

## <a name="rule-sets"></a>規則集

受控碼的程式碼分析規則會分組成「規則集」[](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)。 您可以使用其中一個 Microsoft 標準規則集，也可以 [建立自訂規則集](../code-quality/how-to-create-a-custom-rule-set.md) 來滿足特定需求。

## <a name="suppress-warnings"></a>隱藏警告

最大的用途是指出某個警告不適用。 這會通知程式開發人員和其他稍後可能會檢閱程式碼的人員，指出您已經調查此警告並且隱藏或忽略它。

出現警告的原始檔隱藏會透過自訂屬性來執行。 若要隱藏警告，請將 `SuppressMessage` 屬性加入至原始程式碼，如下列範例所示：

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

如需詳細資訊，請參閱 [隱藏警告](../code-quality/in-source-suppression-overview.md)。

::: moniker range="vs-2017"

> [!NOTE]
> 如果您將專案遷移至 Visual Studio 2017，可能突然遇到大量的程式碼分析警告。 如果您還沒準備好修正這些警告，您可以選擇 [**分析**  >  **執行程式碼分析] 並隱藏** 作用中的問題，來抑制所有警告。
>
> ![在 Visual Studio 中執行程式碼分析和隱藏問題](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> 如果您將專案遷移至 Visual Studio 2019，可能突然遇到大量的程式碼分析警告。 如果您還沒準備好修正這些警告，您可以選擇 [**分析**  >  **組建] 並隱藏** 作用中的問題，來抑制這些警告。

::: moniker-end

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>執行程式碼分析做為簽入原則的一部分

從組織的角度來看，您可能想指定所有的簽入都要滿足特定的原則， 尤其您會想要確認您已經確實遵循這些原則：

- 簽入的程式碼中沒有任何組建錯誤。

- 程式碼分析會以最新組建的一部分來執行。

您可以指定簽入原則，達成上述要求。 如需詳細資訊，請參閱 [使用專案簽入原則強化程式碼品質](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)。

## <a name="team-build-integration"></a>Team build 整合

您可以使用建置系統的整合式功能，執行分析工具做為建置流程的一部分。 如需詳細資訊，請參閱 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)。

## <a name="see-also"></a>另請參閱

- [以 .NET Compiler Platform 為基礎的分析器總覽](../code-quality/roslyn-analyzers-overview.md)
- [使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [如何：啟用和停用自動程式碼分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
