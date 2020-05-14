---
title: 為視覺工作室訂閱者分配特定的 GUID |微軟文件
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/20/2020
ms.topic: conceptual
description: 瞭解管理員如何向訂閱者特定訂閱 GUID
ms.openlocfilehash: e2e8cd4f5d07f218fc23c0b7b6f28ababc25263f
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072589"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>在可視化工作室訂閱管理門戶中分配特定訂閱

管理員現在可以使用可視化工作室訂閱管理門戶將特定訂閱分配給各個訂閱者。  在組織具有需要短期訪問訂閱的臨時員工或供應商的情況下,這非常有用。  管理員可以分配已部分使用的訂閱,將其新訂閱留有供長期使用。  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>使用者配置特定的訂閱 GUID

向個人分配特定訂閱的過程涉及利用兩個現有的管理流程將特定訂閱全域唯一標識符 (GUID) 分配給單個使用者。  三步過程包括匯出當前訂閱和分配的清單,使用該列表標識要分配的特定 GUID,然後使用批量添加過程上傳新分配。

### <a name="export-your-subscriptions-information"></a>匯出訂閱資訊

執行匯出：
1. 登入[管理門戶](https://manage.visualstudio.com)。
2. 選取 [匯出]**** 索引標籤，檔案就會下載到您的本機電腦。 針對包含您使用者訂用帳戶的合約，檔案中會有合約的名稱，以及匯出的日期。
> [!div class="mx-imgBorder"]
> ![匯出訂閱者](_img/exporting-subscriptions/exporting-subscriptions.png)

### <a name="identify-the-guids-you-want-to-assign"></a>確定要配置的 GUID

如果您以前使用過"匯出"工具,您會注意到新欄位已添加到生成的電子錶格中。  這些將説明您確定每個訂閱的狀態以及要分配給使用者的訂閱的狀態。  

- **訂閱狀態**:此欄位將指示"已分配"或"未分配」。  如果訂閱的狀態為"已分配",則該訂閱還將具有與其關聯的使用者資訊,如名稱、電子郵件等。 
- **使用狀態**:使用狀態將指示"新建",這意味著它從未分配給使用者,或"已使用",表明它已分配給使用者在某一點。  

您可以使用這些欄位中的值以及電子表格中的其他資訊來確定要分配給單個使用者的訂閱。 您可以在 Excel 中應用篩選器,以説明按狀態、訂閱等級、到期日期等縮小清單範圍。 

### <a name="upload-your-new-assignments"></a>上傳新工作

最後一步是下載**批量添加**範本,填寫要分配的訂閱所需的資訊,並上傳範本。  有關該過程的完整說明,請參閱我們的[「添加多個使用者」](assign-license-bulk.md)一文。  

> [!IMPORTANT]
> 為確保成功上傳,請確保:
> - 選擇 **「大量新增**」時,正在使用對話框中連結的範本。  不要使用範本的本地存儲副本,因為它可能不包含所有必需的欄位。  使用舊範本將導致上載失敗。 
> - 範本**中顯示的所有**欄位都已完成。
> - **錯誤訊息**列中未列出任何錯誤。
> - 每個 GUID 在範本中只使用一次。 
> - 樣本中的訂閱級別與匯出清單中 GUID 的訂閱匹配。 
> - GUID 尚未分配給匯出清單中的其他使用者。 

## <a name="frequently-asked-questions"></a>常見問題集
### <a name="qhow-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>問:如何更改當前分配給單個使用者的訂閱?
答:如果要更改分配給使用者的 GUID,必須首先刪除該使用者的訂閱。  有關詳細資訊,請參閱我們的["刪除訂閱"](delete-license.md)文章以瞭解更多資訊。  刪除該使用者的訂閱後,請使用上述過程匯出清單並上傳新的訂閱資訊。  

## <a name="see-also"></a>另請參閱
- [視覺化工作室文件](/visualstudio/)
- [Azure 開發人員文件](/azure/devops/)
- [Azure 文件](/azure/)
- [微軟 365 文件](/microsoft-365/)

## <a name="next-steps"></a>後續步驟
現在,您已為使用者分配了訂閱,瞭解如何執行其他管理任務。
- [配置單一訂閱](assign-license.md)
- [配置多個訂閱](assign-license-bulk.md)
- [編輯訂用帳戶](edit-license.md)
- [刪除訂用帳戶](delete-license.md)
- [確定最大使用量](maximum-usage.md)


