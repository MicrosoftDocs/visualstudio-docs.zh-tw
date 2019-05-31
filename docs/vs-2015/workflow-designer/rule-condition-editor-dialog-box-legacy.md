---
title: 規則條件編輯器對話方塊 （舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8237c8e29007d010cd99e4323bf8e88a23b7e9fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006823"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>規則條件編輯器對話方塊 (舊版)
本主題描述如何使用**規則條件編輯器**對話方塊中，在舊版[!INCLUDE[wfd1](../includes/wfd1-md.md)]。 當您需要以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。  
  
 您建立和修改所使用的宣告式規則條件**規則條件編輯器** 對話方塊。 這些規則條件會公開為以下 Windows Workflow Foundation 全新活動中的屬性：  
  
- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
  您存取**規則條件編輯器**對話方塊中，使用[選取條件對話方塊 （舊版）](../workflow-designer/select-condition-dialog-box-legacy.md)。  
  
  下表描述的使用者介面 (UI) 項目**規則條件編輯器** 對話方塊。  
  
|UI 項目|描述|  
|----------------|-----------------|  
|**條件：**|輸入規則條件的運算式。|  
|**[確定]**|按一下以儲存規則條件。|  
  
## <a name="entering-condition-expressions"></a>輸入條件運算式  
 輸入條件運算式為文字。 您可以輸入**這。** 若要參考欄位、 屬性和方法的工作流程中使用編輯器，使用類似 IntelliSense 功能表。 或者您可以直接輸入工作流程成員名稱。 您可以將邏輯運算子新增至條件中，如 AND、OR 和 NOT。 您也可以新增述詞 (Predicate)。 述詞是二元 (Binary) 運算子和兩個運算元。 支援的二元運算子有 **==** ， **>** ， **\<** ， **>=** ，並 **<=** 。 支援的運算元有常數值、算術函式和有範圍的 Public 成員。  
  
 您可以指定的型別進行比較，而且您可以比較與**null**或空字串。 您可以對包含複雜型別之變數上的成員進行巢狀呼叫，例如 `this.Address.State == "WA"`。  
  
 規則條件編輯器支援以下運算子：  
  
- 關係運算子：==、=、!=  
  
- 比較運算子： <， \<=、 >、 > =  
  
- 算術運算子：+、-、*、/、MOD  
  
- 邏輯運算子：AND, &&, OR, &#124;&#124;, NOT, !  
  
- 位元運算子： &，&#124;  
  
  運算式運算子的優先順序是按照 C# 運算子優先順序規則。  
  
  規則條件編輯器支援以下數值運算式：  
  
  this.i == 1D (解析為 1.0)  
  
  this.i == 1E1 (解析為 10.0)  
  
  this.i == 1L (解析為長數值)  
  
  this.i == 1M (解析為小數點)  
  
  this.i == 1F (解析為單一值)  
  
  this.i == 1U (解析為不帶正負號的整數)  
  
  如需有關條件的詳細資訊，請參閱[在工作流程中使用條件](http://go.microsoft.com/fwlink?LinkID=65009)。  
  
## <a name="see-also"></a>另請參閱  
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [選取條件對話方塊 （舊版）](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [工作流程中使用條件](http://go.microsoft.com/fwlink?LinkID=65009)   
 [舊版 Windows Workflow Foundation UI 設計工具的說明](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)