---
title: Domain-Specific Language Tools 概觀
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0962ee3fb780b1634438af48766f2ba086e9f4b2
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="overview-of-domain-specific-language-tools"></a>Domain-Specific Language Tools 概觀
特定領域語言工具 （DSL 工具），裝載在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，讓您設計的特定領域語言，然後產生所有使用者必須具備才能建立模型為基礎之語言的項目。

 DSL 工具包含下列工具：

-   專案精靈會協助您開始開發您的特定領域語言使用不同的解決方案範本。

-   建立和編輯您的特定領域語言定義的圖形設計工具。

-   驗證引擎，以確保網域特定領域語言定義是語式正確，並顯示錯誤和警告，如果有問題。

-   程式碼產生器，會採用做為輸入的網域特定領域語言定義並產生原始程式碼，做為輸出。

## <a name="the-dsl-tools-solution"></a>DSL 工具方案
 定義域專屬 Designer 精靈提供下列解決方案範本：

-   工作流程

-   類別圖表

-   最小的語言

-   元件模型

-   最小的 WPF

-   最小 Windows.Forms

-   DSL 程式庫

 如需詳細資訊，請參閱[選擇特定領域語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。

 精靈會建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]有下列專案的方案：

-   Dsl

     Dsl 專案定義的特定領域語言和其編輯和處理的工具。

-   **DslPackage**

     DslPackage 專案可讓您決定如何語言工具整合與[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。

## <a name="the-dsl-tools-graphical-interface"></a>DSL 工具的圖形化介面
 將項目和關聯性加入至您的特定領域語言，您可以使用 DSL 工具的圖形化介面。 加入項目之後，您可以對應至圖形、 自訂色彩，以及加入裝飾項目來定義其外觀。 您也可以在 [工具箱] 加入項目。

## <a name="validation-in-dsl-tools"></a>DSL 工具中的驗證
 Dsl 提供一個層級的驗證，則請確定網域模型的程式碼產生符合的基本需求。 一般而言，當您建立您自己的特定領域語言，您會加入您自己的驗證，以表達您的商務邏輯規則。 如需有關自訂驗證的詳細資訊，請參閱[中特定領域語言驗證](../modeling/validation-in-a-domain-specific-language.md)。

 我們建議您先通常驗證您的特定領域語言在設計時。 如果您的特定領域語言有驗證錯誤，無法產生原始程式碼。 從範本產生原始程式碼的程序藉由按一下**轉換所有範本** 的 方案總管 工具列中。 每當您修改的語言定義，也請務必**轉換所有範本**。 如需詳細資訊，請參閱[How to： 建立特定領域語言方案](../modeling/how-to-create-a-domain-specific-language-solution.md)。

## <a name="customization-of-dsl-tools"></a>DSL 工具的自訂
 您可以提供額外的程式碼，來精簡模型的行為，並透過您的語言定義條件約束。 必要時，您可以藉由修改文字範本進行重大的變更。

## <a name="distributing-your-dsl-solution"></a>散發 DSL 方案
 DSL 工具會產生裝載中的套件[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 工具箱、 DSL 總管 中和其他 UI 項目，讓使用者可以使用您的特定領域語言建立模型，則會顯示封裝。

 當您建置並執行 DSL 工具方案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，另一個執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]顯示給使用者的語言特定領域語言的外觀。 在您確認一切運作正常之後，您可以將發佈`.vsix`DslPackage 專案的組建資料夾中的檔案。 這個檔案可以用來安裝做為 DSL[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]其他電腦上的擴充功能。  如需詳細資訊，請參閱[部署特定領域語言方案](../modeling/deploying-domain-specific-language-solutions.md)。

## <a name="see-also"></a>另請參閱

- [實驗執行個體](../extensibility/the-experimental-instance.md)
- [特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)