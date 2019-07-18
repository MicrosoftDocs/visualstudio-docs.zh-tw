---
title: 錯誤： 相依性&#39;檔案&#39;專案中&#39;專案&#39;無法複製至執行目錄中，因為它會和相依性衝突&#39;檔案&#39;|Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7726d615c3495845ffdf73d69ffc7d8fae155272
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688269"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>錯誤： 相依性&#39;檔案&#39;專案中&#39;專案&#39;無法複製至執行目錄中，因為它會和相依性衝突&#39;檔案&#39;
參考之間發生衝突；正在將多個同名的相異相依性複製到 bin 目錄，以執行應用程式。 由於沒有相依性是主要參考，因此執行目錄無法解決衝突。  
  
 此錯誤會導致建置失敗。  
  
 按兩下此工作清單項目，可前往發生衝突之專案的參考節點。  
  
 **若要更正這個錯誤**  
  
- 將其中一個組件設為專案的直接參考。 這個方法的可能缺點是，不保證您選擇的組件可以搭配需要其他版本參考組件的組件使用。  
  
     \-或-  
  
- 確定組件的兩個複本都是以強式名稱的方式命名，並且位於全域組件快取中。 如此一來便不需要將組件複製到 bin 目錄。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的參考](../ide/managing-references-in-a-project.md)   
 [全域組件快取](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [強式名稱的組件](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [組件版本控制](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903)   
 [如何：建立及移除專案相依性](../ide/how-to-create-and-remove-project-dependencies.md)