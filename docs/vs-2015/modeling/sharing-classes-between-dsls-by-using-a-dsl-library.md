---
title: 共用使用 DSL 程式庫之間的類別 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0c3a14a254eb3b07a95687faaf377664dd6f747a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942757"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>使用 DSL 程式庫共用 DSL 之間的類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK，您可以建立不完整的 DSL 定義，您可以匯入至另一個 DSL。 這可讓您建構的類似模型的通用部分。  
  
## <a name="creating-and-using-dsl-libraries"></a>建立和使用 DSL 程式庫  
  
#### <a name="to-create-a-dsl-library"></a>若要建立的 DSL 程式庫  
  
1.  建立新的 DSL 專案，並選擇 [DSL 程式庫] 方案範本。  
  
     單一的 DSL 專案將會建立空白的模型。  
  
2.  您可以加入網域類別、 關聯性、 圖形等等。  
  
     文件庫中的項目沒有以形成單一的內嵌樹狀結構中。  
  
     若要定義匯入工具可以使用的關聯性，建立兩個網域類別，並建立其間的關聯性。  
  
     請考慮將**繼承修飾詞**的網域類別`Abstract`。  
  
3.  您可以加入您在 [DSL 總管] 中，例如連接產生器中定義的項目。  
  
4.  您可以新增自訂需要額外的程式碼，例如驗證條件約束。  
  
5.  按一下 **轉換所有範本**。  
  
6.  建置專案。  
  
7.  當您發佈的其他人使用 DSL 時，您必須提供已編譯的組件 (DLL) 和檔案`DslDefinition.dsl`。 您可以在底下的資料夾中找到編譯的組件 `Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>若要匯入的 DSL 程式庫  
  
1. 在另一個 DSL 定義中，在**DSL Explorer**，以滑鼠右鍵按一下 DSL 的根類別，然後按一下**加入新的 DslLibrary 匯入**。  
  
2. 在 [屬性] 視窗中，設定**File-path**程式庫。 您可以使用相對或絕對路徑。  
  
    匯入程式庫會出現在 [DSL 總管] 中，在唯讀模式。  
  
3. 您可以使用匯入的類別作為基底類別。 在匯入的 DSL 中，建立網域類別，然後在 [屬性] 視窗中，將**基底類別**匯入的類別。  
  
4. 按一下 轉換所有範本。  
  
5. DSL 程式庫專案所建置的組件 (DLL) 的參考加入至 DSL 專案中。  
  
6. 建置方案。  
  
   DSL 程式庫可以匯入其他程式庫。 當您匯入程式庫時，其匯入也會自動出現在 [DSL 總管] 中。  
  
## <a name="see-also"></a>另請參閱  
 [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)
