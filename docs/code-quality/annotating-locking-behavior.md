---
title: 註釋鎖定行為
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 21c67bb8b99c2772e107ded9063a99940a7fac74
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="annotating-locking-behavior"></a>註釋鎖定行為
為了避免多執行緒程式中發生並行 Bug，請務必遵循適當的鎖定規範並使用 SAL 註釋。

 並行 Bug 極難重新產生、診斷和偵錯，因為他們並非決定性的 Bug。 如果您要設計的程式碼主體包含許多執行緒，那麼要找出造成執行緒交錯的原因更是困難且不實際。 因此，較好的做法是遵循多執行緒程式中的鎖定規範。 例如，當擷取多個鎖定時遵循鎖定順序有助於避免發生死結，而在存取共用資源之前取得適當防護的鎖定有助於避免產生競爭條件。

 可惜的是，看似簡單的鎖定規則在實務上可能非常不容易遵循。 在現今的程式設計語言和編譯器的基本限制是，它們不直接支援的規格和分析的並行需求。 程式設計人員必須依賴非正式的程式碼註解來表達其使用鎖定的目的。

 並行 SAL 註釋的設計在於幫助您指定鎖定的副作用、鎖定責任、資料保護、鎖定順序階層，以及其他必要的鎖定行為。 SAL 並行註釋藉由讓隱含規則變為明確，提供了一致的方式讓您記錄程式碼使用鎖定規則的方式。 並行註釋還可以增強程式碼分析工具的能力，找出競爭條件、死結、不相符的同步處理作業及其他細小的並行錯誤。

## <a name="general-guidelines"></a>一般方針
 藉由使用註釋，您可以陳述實作 (被呼叫者) 和用戶端 (呼叫端) 之間由函式定義隱含的合約，以及表達可進一步改善分析的非變異項目和其他程式屬性。

 SAL 支援多種不同的鎖定基本類型，例如關鍵區段、Mutex、微調鎖定和其他資源物件。 許多並行註釋需要參數將鎖定運算式。 依照慣例，鎖定為基礎的鎖定物件的路徑運算式所表示。

 請記住一些執行緒擁有權規則：

-   微調鎖定是擁有清楚執行緒擁有權的不可計數鎖定。

-   Mutex 和關鍵區段是擁有清楚執行緒擁有權的計數鎖定。

-   信號和事件是未擁有清楚執行緒擁有權的計數鎖定。

## <a name="locking-annotations"></a>鎖定的註解
 下表列出的鎖定的註解。

|註釋|描述|
|----------------|-----------------|
|`_Acquires_exclusive_lock_(expr)`|為函式加上附註，並指出在後製狀態下，函式會讓 `expr` 命名之鎖定物件的獨佔鎖定計數遞增 1。|
|`_Acquires_lock_(expr)`|為函式加上附註，並指出在後製狀態下，函式會讓 `expr` 命名之鎖定物件的鎖定計數遞增 1。|
|`_Acquires_nonreentrant_lock_(expr)`|取得由 `expr` 命名的鎖定。  如果鎖定已保留，則會報告錯誤。|
|`_Acquires_shared_lock_(expr)`|為函式加上附註，並指出在後製狀態下，函式會讓 `expr` 命名之鎖定物件的共用鎖定計數遞增 1。|
|`_Create_lock_level_(name)`|將符號 `name` 宣告為鎖定層級的陳述式，如此該符號就可以在註釋 `_Has_Lock_level_` 和 `_Lock_level_order_` 中使用。|
|`_Has_lock_kind_(kind)`|加上附註來精簡的資源物件的型別資訊的任何物件。 有時候一般型別用於不同種類的資源和多載的型別不是足以區別各種資源之間的語意需求。 以下是預先定義的 `kind` 參數清單：<br /><br /> `_Lock_kind_mutex_`<br /> Mutex 鎖定類型識別碼。<br /><br /> `_Lock_kind_event_`<br /> 鎖定事件種類的識別碼。<br /><br /> `_Lock_kind_semaphore_`<br /> 號誌鎖定類型識別碼。<br /><br /> `_Lock_kind_spin_lock_`<br /> 微調鎖定的鎖定類型識別碼。<br /><br /> `_Lock_kind_critical_section_`<br /> 關鍵區段的鎖定類型識別碼。|
|`_Has_lock_level_(name)`|為鎖定物件加上附註，並為其指定 `name` 的鎖定層級。|
|`_Lock_level_order_(name1, name2)`|陳述式，為鎖定之間的順序`name1`和`name2`。|
|`_Post_same_lock_(expr1, expr2)`|為函式加上附註，並指出並後製狀態下，`expr1` 和 `expr2` 這兩個鎖定會視為是相同的鎖定物件。|
|`_Releases_exclusive_lock_(expr)`|為函式加上附註，並指出在後製狀態下，函式會讓 `expr` 命名之鎖定物件的獨佔鎖定計數遞減 1。|
|`_Releases_lock_(expr)`|為函式加上附註，並指出在後製狀態下，函式會讓 `expr` 命名之鎖定物件的鎖定計數遞減 1。|
|`_Releases_nonreentrant_lock_(expr)`|會釋放由 `expr` 命名的鎖定。 如果目前沒有保留鎖定，則會報告錯誤。|
|`_Releases_shared_lock_(expr)`|為函式加上附註，並指出在後製狀態下，函式會讓 `expr` 命名之鎖定物件的共用鎖定計數遞減 1。|
|`_Requires_lock_held_(expr)`|為函式加上附註，並指出在前置狀態下，由 `expr` 命名之物件的鎖定計數至少為一。|
|`_Requires_lock_not_held_(expr)`|為函式加上附註，並指出在前置狀態下，由 `expr` 命名之物件的鎖定計數為零。|
|`_Requires_no_locks_held_`|標註函式，並指出檢查程式已知之所有鎖定的鎖定計數為零。|
|`_Requires_shared_lock_held_(expr)`|為函式加上附註，並指出在前置狀態下，由 `expr` 命名之物件的共用鎖定計數至少為一。|
|`_Requires_exclusive_lock_held_(expr)`|為函式加上附註，並指出在前置狀態下，由 `expr` 命名之物件的獨佔鎖定計數至少為一。|

## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>未公開之鎖定物件的 SAL 內在變數
 某些鎖定物件不會由相關聯的鎖定函式的實作來公開。  下表列出 SAL 內部變數，這些變數會啟用在未公開的鎖定物件上運作之函式的註釋。

|註釋|描述|
|----------------|-----------------|
|`_Global_cancel_spin_lock_`|描述取消微調鎖定。|
|`_Global_critical_region_`|描述關鍵區域。|
|`_Global_interlock_`|描述連鎖作業。|
|`_Global_priority_region_`|描述優先權區域。|

## <a name="shared-data-access-annotations"></a>共用的資料存取註解
 下表列出共用資料存取的註釋。

|註釋|描述|
|----------------|-----------------|
|`_Guarded_by_(expr)`|為變數加上附註，並指出只要存取變數，由 `expr` 命名之鎖定物件的鎖定計數就會至少為一。|
|`_Interlocked_`|標註變數，而且相當於`_Guarded_by_(_Global_interlock_)`。|
|`_Interlocked_operand_`|標註函式參數是一個不同的連鎖函式的目標運算元。  這些運算元必須有特定的其他屬性。|
|`_Write_guarded_by_(expr)`|為變數加上附註，並指出只要修改變數，由 `expr` 命名之鎖定物件的鎖定計數就會至少為一。|

## <a name="see-also"></a>另請參閱
 [使用 SAL 註釋減少 C/c + + 程式碼缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)[了解 SAL](../code-quality/understanding-sal.md) [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)[註釋函式行為](../code-quality/annotating-function-behavior.md)[註釋結構和類別](../code-quality/annotating-structs-and-classes.md)[指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)[內建函式](../code-quality/intrinsic-functions.md)[最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)[程式碼分析小組部落格](http://go.microsoft.com/fwlink/p/?LinkId=251197)