---
title: 網域路徑語法 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d4e98715bae8869619e8d9f2852c810153984777
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254770"
---
# <a name="domain-path-syntax"></a>網域路徑語法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL 定義使用類似 XPath 的語法來尋找模型中的特定項目。  
  
 您通常不需要直接使用這個語法。 [DSL 詳細資料] 或 [屬性] 視窗中會顯示這個語法，您可以在視窗中按一下向下箭號並使用路徑編輯器。 不過，在使用編輯器之後，路徑會以下列格式顯示在欄位中。  
  
 網域路徑的格式如下：  
  
 *RelationshipName.PropertyName/!Role*  
  
 ![CommentReferencesSubjects 參考關聯性](../modeling/media/dsl-reference.png "dsl_reference")  
  
 這個語法會周遊模型的樹狀結構。 例如，網域關聯性**CommentReferencesSubjects**上圖中有**主體**角色。 路徑區段 **/ ！Subjectt**指定的路徑是透過存取的項目上完成**科目**角色。  
  
 每個區段以網域關聯性的名稱開頭。 周遊關聯性是從項目，如果路徑區段會顯示為*Relationship.PropertyName*。 如果躍點，從連結的項目路徑區段會顯示為*關聯性 / ！RoleName*。  
  
 請以斜線分隔路徑的語法。 每個路徑區段可以是項目到連結的躍點 (關聯性執行個體) 或連結到項目的躍點。 路徑區段經常會成對顯示。 一個路徑區段表示項目到連結的躍點，下一個區段表示連結到項目的反向躍點。 (任何連結也可以是關聯性本身的來源或目標)。  
  
 用於表示項目到連結之躍點的名稱是角色的 [`Property Name`] 值。 用於表示連結到項目之躍點的名稱是目標角色名稱。  
  
## <a name="see-also"></a>另請參閱  
 [了解模型、類別和關聯性](../modeling/understanding-models-classes-and-relationships.md)



