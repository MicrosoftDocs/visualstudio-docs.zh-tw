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
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6942511e325b77aaa3d646b6e84cd833b8b55ab2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871741"
---
# <a name="overview-of-domain-specific-language-tools"></a>Domain-Specific Language Tools 概觀
特定領域語言工具 （DSL 工具），其裝載在 Visual Studio 中，可讓您設計的特定領域語言，然後再產生所有使用者必須具備才能建立模型為基礎之語言的項目。

 DSL 工具包含下列工具：

-   使用不同的解決方案範本來協助您開始開發您的網域特定語言專案精靈。

-   建立和編輯您的特定領域語言定義的圖形化設計工具。

-   驗證引擎，可確保特定領域語言定義的格式正確，並顯示錯誤和警告，如果有問題。

-   程式碼產生器會做為輸入的特定領域語言定義，並產生原始程式碼，做為輸出。

## <a name="the-dsl-tools-solution"></a>DSL 工具解決方案
 定義域專屬設計工具精靈提供下列的解決方案範本：

- 工作流程

- 類別圖表

- 最小語言

- 元件模型

- 最小 WPF

- 最小 Windows.Forms

- DSL 程式庫

  如需詳細資訊，請參閱 <<c0> [ 選擇特定領域語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。

  精靈會建立含有下列專案的 Visual Studio 方案：

- Dsl

   Dsl 專案中定義特定領域語言，以及其編輯和處理工具。

- **DslPackage**

   在 DslPackage 專案決定語言工具如何與 Visual Studio 整合。

## <a name="the-dsl-tools-graphical-interface"></a>DSL 工具的圖形化介面
 若要將項目和關聯性新增至您的特定領域語言，您可以使用 DSL 工具的圖形化介面。 加入項目之後，您可以將它們對應至圖形、 自訂色彩，以及加入裝飾項目來定義其外觀。 您也可以將項目加入 [工具箱] 中。

## <a name="validation-in-dsl-tools"></a>DSL 工具中的驗證
 Dsl 提供一個層級的驗證，請確定網域模型產生程式碼符合基本需求。 一般而言，當您建立您自己的特定領域語言，您會新增您自己的驗證，以表達您的商務邏輯規則。 如需有關自訂驗證的詳細資訊，請參閱 <<c0> [ 定義域專屬語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)。

 我們建議您先通常驗證您的特定領域語言在設計時。 如果您的特定領域語言有驗證錯誤，您就無法產生原始程式碼。 從範本產生程式碼的程序會依序按一下**轉換所有範本** 工具列中的 方案總管 中。 每當您修改語言定義，也請務必**轉換所有範本**。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立特定領域語言方案](../modeling/how-to-create-a-domain-specific-language-solution.md)。

## <a name="customization-of-dsl-tools"></a>自訂的 DSL 工具
 您可以提供額外的程式碼，來精簡模型的行為，並透過您的語言定義條件約束。 如有需要，您可以藉由修改文字範本中進行重大的變更。

## <a name="distributing-your-dsl-solution"></a>散發您的 DSL 方案
 DSL 工具會在 Visual Studio 中產生裝載的套件。 工具箱、 DSL 總管 中和其他 UI 元素，讓使用者使用特定領域語言建立模型，則會顯示封裝。

 當您建置並執行 DSL 工具方案在 Visual Studio 中時，Visual Studio 的第二個執行個體顯示給使用者的語言特定領域語言的外觀。 在確認一切都運作正常之後，您可以將散發`.vsix`您會發現在 DslPackage 專案的組建資料夾中的檔案。 此檔案可用來做為 Visual Studio 擴充功能，在其他電腦上安裝 DSL。  如需詳細資訊，請參閱 <<c0> [ 部署特定領域語言方案](../modeling/deploying-domain-specific-language-solutions.md)。

## <a name="see-also"></a>另請參閱

- [實驗執行個體](../extensibility/the-experimental-instance.md)
- [特定領域語言工具字彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)