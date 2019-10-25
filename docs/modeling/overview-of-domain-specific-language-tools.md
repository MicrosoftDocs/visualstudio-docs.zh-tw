---
title: Domain-Specific Language Tools 概觀
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82bccbd9558a5dad87e9fe13f9ed7136a5d77d8a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747516"
---
# <a name="overview-of-domain-specific-language-tools"></a>Domain-Specific Language Tools 概觀
Visual Studio 所裝載的特定領域語言工具（DSL 工具），可讓您設計特定領域語言，然後產生使用者建立以該語言為基礎之模型所需的所有專案。

 DSL 工具中包含下列工具：

- 專案精靈，使用不同的方案範本來協助您開始開發特定領域語言。

- 圖形化設計工具，用於建立和編輯特定領域語言定義。

- 驗證引擎，確保特定領域語言定義的語式正確，並在發生問題時顯示錯誤和警告。

- 程式碼產生器，接受特定領域語言定義作為輸入，並產生原始程式碼作為輸出。

## <a name="the-dsl-tools-solution"></a>DSL 工具方案
 [特定領域設計工具精靈] 提供下列方案範本：

- 工作流程

- 類別圖表

- 最小語言

- 元件模型

- 最小 WPF

- 最小 Windows.Forms

- DSL 程式庫

  如需詳細資訊，請參閱[選擇特定領域語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。

  此 wizard 會建立包含下列專案的 Visual Studio 方案：

- DSL

   DSL 專案會定義特定領域語言，以及其編輯和處理工具。

- **DslPackage**

   DslPackage 專案會決定語言工具如何與 Visual Studio 整合。

## <a name="the-dsl-tools-graphical-interface"></a>DSL 工具圖形化介面
 您可以使用 DSL 工具圖形化介面，將項目和關聯新增至您的特定領域語言。 新增項目之後，您可以將其對應至圖形、自訂色彩和新增裝飾項目，來定義其外觀。 您也可以將項目新增至 [工具箱]。

## <a name="validation-in-dsl-tools"></a>DSL 工具中的驗證
 Dsl 提供一層驗證來確保領域模型符合產生程式碼的基本需求。 一般而言，當您建立自己的特定領域語言時，您會新增自己的驗證來表示商務邏輯規則。 如需自訂驗證的詳細資訊，請參閱[特定領域語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)。

 建議您在設計特定領域語言時經常進行驗證。 如果您的特定領域語言發生驗證錯誤，則無法產生原始程式碼。 在 [方案總管] 的工具列中按一下 [轉換所有範本]，以執行從範本產生原始程式碼的程序。 每當您修改語言定義時，也請務必**轉換所有範本**。 如需詳細資訊，請參閱[如何：建立特定領域語言方案](../modeling/how-to-create-a-domain-specific-language-solution.md)。

## <a name="customization-of-dsl-tools"></a>DSL 工具自訂
 您可以提供其他程式碼來精簡模型的行為，以及定義語言的條件約束。 如有需要，您可以修改文字範本來進行大幅變更。

## <a name="distributing-your-dsl-solution"></a>散發您的 DSL 方案
 DSL 工具會產生裝載于 Visual Studio 中的封裝。 此套件會顯示 [工具箱]、[DSL 總管] 和其他 UI 項目，讓使用者可以使用您的特定領域語言來建立模型。

 當您在 Visual Studio 中建立並執行 DSL 工具方案時，Visual Studio 的第二個實例會向您顯示特定領域語言對語言使用者的外觀。 確認一切運作正常之後，您就可以散發在 DslPackage 專案組建資料夾中找到的 `.vsix` 檔案。 這個檔案可以用來將 DSL 安裝在其他電腦上做為 Visual Studio 擴充功能。  如需詳細資訊，請參閱[部署特定領域語言方案](msi-and-vsix-deployment-of-a-dsl.md)。

## <a name="see-also"></a>請參閱

- [實驗執行個體](../extensibility/the-experimental-instance.md)
- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)