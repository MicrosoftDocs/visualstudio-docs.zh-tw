---
title: Visual Studio 訂用帳戶中的 Microsoft Windows 虛擬桌面 |Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 12/02/2020
ms.topic: conceptual
description: 瞭解如何透過您的 Visual Studio 訂用帳戶來利用 Microsoft Windows 虛擬桌面
ms.openlocfilehash: 9198f4180a2f98b89540f1eedc0dab4be59558ab
ms.sourcegitcommit: 29099741fcf94a5aef2655ee16605728b8b9a0ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96537951"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>存取訂用帳戶中的 Windows 虛擬桌面 
Visual Studio 訂閱者現在可以將其 Azure 開發/測試人員點數用於 Microsoft Windows 虛擬桌面服務。  
Windows 虛擬桌面是在雲端中執行的全方位桌面與應用程式虛擬化服務。 它是唯一 (VDI) 的虛擬桌面基礎結構，可提供簡化的管理、多重會話 Windows 10、適用于企業的 Microsoft 365 應用程式優化，以及遠端桌面服務 (RDS) 環境的支援。 幾分鐘內即可在 Azure 上部署及調整您的 Windows 桌面和應用程式，並取得內建的安全性和合規性功能。
以下是您在 Azure 上執行 Windows 虛擬桌面時可以執行的作業：
- 設定多工作階段的 Windows 10 部署，以提供具有延展性的完整 Windows 10
- 將 Microsoft 365 Apps 企業版虛擬化，並將其最佳化以在多使用者的虛擬案例中執行
- 提供具有免費擴充安全性更新的 Windows 7 虛擬桌面
- 將您現有的遠端桌面服務 (RDS) 和 Windows Server 桌面和應用程式帶到任何電腦
- 將桌面和應用程式虛擬化
- 使用統一的管理體驗來管理 Windows 10、Windows Server 和 Windows 7 桌上型電腦和應用程式，以瞭解您可以如何使用 Windows 虛擬桌面的詳細資訊，請觀看 [簡介影片](/azure/virtual-desktop/overview)。

## <a name="use-windows-virtual-desktop-with-azure"></a>搭配 Azure 使用 Windows 虛擬桌面 
Visual Studio 訂閱者現在有數種方式可使用 Azure 訂用帳戶來支付 Windows 虛擬桌面服務的費用：
- [Azure DevTest 個別點數](vs-azure.md)。  在訂用帳戶中收到 Azure DevTest 個別點數的訂閱者可以使用這些信用額度來支付 Windows 虛擬桌面服務的費用。  每月信用額度的金額取決於訂用帳戶層級。
- [Azure DevTest 隨用隨付訂用](vs-azure-payg.md)帳戶。  您可以建立 Azure 訂用帳戶並附加付款條件，讓您有順暢的方式來為您的 Windows 虛擬桌面使用量付費。 
- [Azure Enterprise 合約 DevTest 優惠](azure-ea-devtest.md)。  有了這種供應專案，具有 Enterprise 合約的訂閱者可以用折扣價格支付 Azure 的 Windows 虛擬桌面費用。 

## <a name="requirements"></a>需求
Windows 虛擬桌面需要 Azure Active Directory (Azure AD) 將會聯結 Vm。  使用者必須是此 Azure AD 的成員。  有兩個選項可執行 Azure AD：
- Azure AD 目錄服務。  對於大部分的使用者而言，這是最容易執行的選項。
- 執行網域控制站促銷的虛擬機器。  此選項需要更多的工作來設定，但可為大多數使用者提供較低的營運成本。
若要查看使用 Windows 虛擬桌面之必要條件的完整清單，請流覽 Windows 虛擬桌面的 [[總覽] 頁面](/azure/virtual-desktop/overview#requirements)。 

## <a name="get-started"></a>開始使用 
當您的所有必要條件都已就緒時，您會想要完成數個動作來準備您的實施。  若要開始使用，請參閱下列教學課程：
- [建立 Windows 虛擬桌面租用戶](/azure/virtual-desktop/virtual-desktop-fall-2019/tenant-setup-azure-active-directory)
- 使用 Azure 入口網站[建立主機集](/azure/virtual-desktop/create-host-pools-azure-marketplace)區
- 管理適用于 Windows 虛擬桌面的[應用程式群組](/azure/virtual-desktop/manage-app-groups)

## <a name="eligibility"></a>資格
| 訂用帳戶層級                                                 |     通道                                            | 優點                                                          | 可續約？    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | VL, Azure, 零售, | 可用|  是          |
| 使用 GitHub Enterprise Visual Studio Enterprise 訂用帳戶  | Vl | 可用|  是          |
| Visual Studio Professional (Standard) | VL, Azure, 零售                                       | 可用                                                             |  是             |
| 使用 GitHub Enterprise Visual Studio Professional 訂用帳戶 | Vl                                       | 可用                                        |  是           |
| Visual Studio Test Professional (標準訂用帳戶)                         | VL, 零售                                              | 可用|  是          |
| MSDN 平台 (標準)                                          | VL, 零售                                              | 可用                                         |  是          |
| Visual Studio Enterprise (Standard)  | NFR<sup>1</sup> |無法使用  | N/A |
| Visual Studio Enterprise、Visual Studio Professional (每月雲端) | Azure | 無法使用 | N/A |

<sup>1</sup>  *包括：禁止轉售 (NFR) 、FTE、最有價值專家 (MVP) 、區域主管 (RD) 、Microsoft 合作夥伴網路 (MPN) 、Visual Studio 產業合作夥伴 (VSIP) 、Microsoft 認證訓練人員、BizSpark、設想*

> [!NOTE]
> Microsoft 不再於雲端訂用帳戶中提供 Visual Studio Professional 年度訂用帳戶和 Visual Studio Enterprise 年度訂用帳戶。 現有的客戶體驗，以及更新、增加、減少或取消其訂用帳戶的能力將不會改變。 建議新客戶移至，以 [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) 探索購買 Visual Studio 的不同選項。

不確定您使用哪一個訂用帳戶？  連接至以 [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) 查看指派給您電子郵件地址的所有訂用帳戶。 若沒有看到您的所有訂用帳戶，可能有一或多個訂用帳戶是指派到不同的電子郵件地址。  您必須以該電子郵件地址登入才能查看對應的訂用帳戶。

## <a name="see-also"></a>請參閱
- [Azure 檔](/azure/)
- [Windows 虛擬桌面文件](/azure/virtual-desktop/)

## <a name="next-steps"></a>後續步驟
-   如果您需要購買 Visual Studio 訂閱，請參閱：
     - 透過 Microsoft Store 的[零售購買定價](https://visualstudio.microsoft.com/vs/pricing/)
     - [大量授權方案](https://www.microsoft.com/licensing/default)
-   深入瞭解 [Windows 虛擬桌面](/azure/virtual-desktop/overview)