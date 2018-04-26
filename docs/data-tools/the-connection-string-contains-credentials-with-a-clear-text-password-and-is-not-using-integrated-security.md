---
title: 連接字串包含具有純文字密碼的認證，並且不使用整合式安全性
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: bf8a8fc3bb024c1eb8ee7baf91856a54dcb9d21f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>連接字串包含具有純文字密碼的認證，並且不使用整合式安全性

是否要將連接字串連同這些敏感資訊一起儲存到目前的 DBML 檔案和應用程式組態檔？  按 [否] 會只儲存連接字串，不會儲存敏感資訊。

使用內含敏感資訊 (含在連接字串中的密碼) 的資料連接時，可以選擇是否在將連接字串儲存至專案的 DBML 檔案和應用程式組態檔時包含敏感資訊。

> [!WARNING]
> 明確設定**連接**屬性**應用程式設定**屬性**False**會將密碼加入到 DBML 檔案。

## <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>若要將連接字串連同敏感資訊一起儲存到專案的應用程式設定中

- 按一下 [ **是**]。

   連接字串會儲存為應用程式設定。 連接字串會包含純文字的敏感資訊。 DBML 檔案不包含敏感資訊。

## <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>若要將連接字串儲存到專案的應用程式設定中，但不儲存敏感資訊

- 按一下 [否] 。

   連接字串會儲存為應用程式設定，但是不包含密碼。

## <a name="see-also"></a>另請參閱

- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)