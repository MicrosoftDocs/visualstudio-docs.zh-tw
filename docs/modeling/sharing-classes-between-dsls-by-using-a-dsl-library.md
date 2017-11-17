---
title: "共用類別之間使用 DSL 庫 Dsl |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: "7"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: ed225f315c92cf9276eb97fcb78e1730250ecd4c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>使用 DSL 程式庫共用 DSL 之間的類別
在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Visualization and Modeling SDK，您可以建立不完整，您可以匯入另一個 DSL DSL 定義。 這可讓您因素的類似模型的通用部分。  
  
## <a name="creating-and-using-dsl-libraries"></a>建立和使用 DSL 程式庫  
  
#### <a name="to-create-a-dsl-library"></a>若要建立 DSL 文件庫  
  
1.  建立新的 DSL 專案，並選擇 DSL 文件庫方案範本。  
  
     單一 DSL 專案將會建立空的模型。  
  
2.  您可以加入網域類別、 關聯性、 圖形等等。  
  
     文件庫中的項目沒有形成單一的內嵌樹狀結構。  
  
     若要定義匯入工具可以使用的關聯性，建立兩個網域類別並建立它們之間的關聯性。  
  
     請考慮設定**繼承修飾詞**網域類別，來`Abstract`。  
  
3.  您可以加入您在 DSL 總管 中，例如連接產生器中定義的項目。  
  
4.  您可以將需要額外的程式碼，例如驗證條件約束的自訂內容。  
  
5.  按一下**轉換所有範本**。  
  
6.  建置專案。  
  
7.  當您發佈其他人使用的 DSL 時，您必須提供已編譯的組件 (DLL) 和檔案`DslDefinition.dsl`。 您可以在資料夾下找到編譯的組件`Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>若要匯入 DSL 程式庫  
  
1.  在另一個 DSL 定義中，在**DSL 總管**，DSL 的根類別上按一下滑鼠右鍵，然後按一下**加入 DslLibrary 匯入**。  
  
2.  在 [屬性] 視窗中，設定**檔案路徑**程式庫。 您可以使用相對或絕對路徑。  
  
     匯入程式庫會出現在 DSL 總管中，以唯讀模式。  
  
3.  您可以使用匯入的類別作為基底類別。 在匯入的 DSL，建立網域類別，並在 [屬性] 視窗中，將**基底類別**匯入的類別。  
  
4.  按一下 轉換所有範本。  
  
5.  DSL 專案中加入 DSL 程式庫專案所建置之組件 (DLL) 的參考。  
  
6.  建置方案。  
  
 DSL 程式庫可以匯入其他程式庫。 當您匯入程式庫，其匯入也會自動出現在 DSL 總管 中。  
  
## <a name="see-also"></a>另請參閱  
 [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
