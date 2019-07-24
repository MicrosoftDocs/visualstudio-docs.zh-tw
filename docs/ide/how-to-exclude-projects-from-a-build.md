---
title: 作法：從組建排除專案
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54e65c411afe9815696112dfbcc99bcb9433c4db
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416861"
---
# <a name="how-to-exclude-projects-from-a-build"></a>作法：從組建排除專案

您可以建置方案，而不建置它所包含的所有專案。 例如，您可能會排除會中斷組建的專案。 然後您可以在調查和處理這些問題之後才建置專案。

您可以利用下列方式排除專案：

- 從作用中的方案組態暫時將其移除。

- 建立不包含專案的方案組態。

如需詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>從作用中的方案組態暫時將專案移除

1. 在功能表列上，選擇 [建置]   > [組態管理員]  。

2. 在 [專案內容]  資料表中，找出您想要從組建排除的專案。

3. 在專案的 [組建]  資料行中，清除核取方塊。

4. 選擇 [關閉]  按鈕，然後重新建置方案。

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>建立排除專案的方案組態

1. 在功能表列上，選擇 [建置]   > [組態管理員]  。

2. 在 [使用中的方案組態]  清單中，選擇 [\<新增>]  。

3. 在 [名稱]  方塊中，輸入方案組態的名稱。

4. 在 [複製設定來源]  清單中，選擇您要以其為新組態根據的方案組態 (例如，偵錯  )，然後選擇 [確定]  按鈕。

5. 在 [組態管理員]  對話方塊中，清除 [建置]  資料行中您想要排除之專案的核取方塊，然後選擇 [關閉]  按鈕。

6. 在 [標準]  工具列上，確認新的方案組態是 [方案組態]  方塊中的使用中組態。

7. 在功能表列上，依序選擇 [建置]   > [重建方案]  。

## <a name="see-also"></a>另請參閱

- [了解建置組態](../ide/understanding-build-configurations.md)
- [操作說明：建立及編輯組態](../ide/how-to-create-and-edit-configurations.md)
- [操作說明：同時建置多個組態](../ide/how-to-build-multiple-configurations-simultaneously.md)