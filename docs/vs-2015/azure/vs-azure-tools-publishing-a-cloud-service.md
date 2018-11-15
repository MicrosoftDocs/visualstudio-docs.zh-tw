---
title: 發佈雲端服務使用 Azure Tools |Microsoft Docs
description: 深入了解如何使用 Visual Studio 發佈 Azure 雲端服務專案。
author: ghogen
manager: douge
assetId: 1a07b6e4-3678-4cbf-b37e-4520b402a3d9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: cf29e1cdde71d2e8ef7caa9bc91bc31c30c7bc41
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001956"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>使用 Visual Studio 來發佈雲端服務

Visual Studio 可以發行應用程式直接部署至 Azure，雲端服務的預備和生產環境的支援。 發佈時，您可以選取的部署環境及部署套件暫時使用的儲存體帳戶。

當您開發並測試 Azure 應用程式時，您可以使用 Web Deploy 以累加方式對 web 角色發佈變更。 您發行至部署環境的應用程式之後，Web Deploy 可讓您變更直接部署到虛擬機器正在執行 web 角色。 您不必在封裝和發佈整個 Azure 應用程式每次您想要更新您的 web 角色，來測試所做的變更。 使用此方法時，您可以在雲端進行測試，而不等候您的應用程式發佈至部署環境中有提供 web 角色變更。

將發佈 Azure 應用程式，並使用 Web Deploy 更新 web 角色，請使用下列程序：

- 發行或封裝 Azure 應用程式從 Visual Studio
- 更新 web 角色一部分的開發和測試週期

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>發行或封裝 Azure 應用程式從 Visual Studio

當您發行 Azure 應用程式時，您可以執行下列工作之一：

- 建立服務封裝： 您可以使用此封裝和服務組態檔至應用程式發佈至部署環境，從[Azure 入口網站](https://portal.azure.com)。

- 發行 Azure 專案從 Visual Studio： 若要發佈您的應用程式直接部署至 Azure，您可以使用 [發行精靈]。 如需資訊，請參閱[發佈 Azure 應用程式精靈](vs-azure-tools-publish-azure-application-wizard.md)。

### <a name="to-create-a-service-package-from-visual-studio"></a>若要從 Visual Studio 中建立服務封裝

1. 準備好要發行應用程式時，開啟 [方案總管] 中開啟包含您的角色的 Azure 專案的捷徑功能表，選擇 [發佈]。

1. 若要建立服務封裝，請遵循下列步驟：

   a. 在 Azure 專案的捷徑功能表，選擇**封裝**。

   b. 在 **封裝 Azure 應用程式** 對話方塊中，選擇您要建立封裝時，服務組態，然後選擇 組建組態。

   c.  （選擇性）若要開啟遠端桌面的雲端服務在發行後，請選取**啟用所有角色的遠端桌面**，然後選取**設定**來設定遠端桌面認證。 如需詳細資訊，請參閱 <<c0> [ 使用 Visual Studio 的 Azure 雲端服務中的角色啟用遠端桌面連線](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio)。

      如果您想要偵錯雲端服務，在發行後，開啟所選取的遠端偵錯**啟用遠端偵錯工具的所有角色**。

   d. 若要建立封裝時，選擇**封裝**連結。

      檔案總管 會顯示新建立的封裝的檔案位置。 您可以複製這個位置，好讓您可以使用它從 Azure 入口網站。

   e. 若要將此封裝發佈至部署環境中，您必須為封裝位置使用此位置，當您建立雲端服務，並將此封裝部署至 Azure 入口網站的環境。

1. （選擇性）若要取消部署程序，在活動記錄檔中的細目的捷徑功能表上選擇**取消並移除**。 此命令會停止部署程序，並從 Azure 刪除部署環境。 若要在部署後移除環境，使用 Azure 入口網站。

1. （選擇性）您的角色執行個體啟動後，Visual Studio 會自動顯示部署環境**雲端服務**伺服器總管 中的節點。 從這裡開始，您可以看到個別角色執行個體的狀態。 請參閱[使用雲端總管管理 Azure 資源](vs-azure-tools-resources-managing-with-cloud-explorer.md)。下圖顯示角色執行個體，而仍處於初始化狀態：

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>更新 web 角色一部分的開發和測試週期

如果您的應用程式後端基礎結構很穩定，但 web 角色需要更頻繁的更新，您可以使用 Web Deploy 更新 web 角色專案中。 當您不想要重建並重新部署後端背景工作角色，或如果您有多個 web 角色，而且您想要更新其中一個 web 角色，web Deploy 很方便。

### <a name="requirements-for-using-web-deploy"></a>使用 Web Deploy 的需求

- **只能用於開發和測試目的**: 會直接對變更虛擬機器正在執行 web 角色。 如果此虛擬機器必須回收，因為您發佈的原始套件用來重新建立角色的虛擬機器所做的變更都會遺失。 重新發佈您的應用程式 web 角色取得的最新的變更。

- **只有 web 角色可以更新**： 無法更新背景工作角色。 此外，您不能更新`RoleEntryPoint`在`web role.cs`。

- **只能支援 web 角色的單一執行個體**： 您無法部署環境中有任何 web 角色的多個執行個體。 不過，支援多個 web 角色每一個只有一個執行個體。

- **啟用遠端桌面連線**： 這項需求讓 Web Deploy 使用使用者名稱和密碼來連線到虛擬機器，將變更部署到執行 Internet Information Services (IIS) 伺服器。 此外，您可能需要連接到虛擬機器新增至 IIS 的受信任的憑證，此虛擬機器上。 （此憑證可確保 Web Deploy 所使用的 IIS 的遠端連線安全無虞。）

下列程序假設您使用**發佈 Azure 應用程式**精靈。

### <a name="enable-web-deploy-when-you-publish-your-application"></a>啟用 Web Deploy 發行應用程式時

1. 若要啟用**為所有 web 角色啟用 Web Deploy**選項時，您必須先設定遠端桌面連線。 選取 **啟用遠端桌面**所有角色，然後提供用來從遠端在連接的認證**遠端桌面組態**出現方塊。 請參閱[使用 Visual Studio 的 Azure 雲端服務中的角色啟用遠端桌面連線](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio)。

1. 若要啟用 Web Deploy 應用程式中的所有 web 角色，請選取**為所有 web 角色都啟用 Web Deploy**。

    此時會出現黃色警告三角形。 Web Deploy 使用不受信任、 自我簽署憑證根據預設，不建議用於上傳機密資料。 如果您需要保護機密資料進行此程序，您可以新增 SSL 憑證來用於 Web Deploy 連線。 此憑證必須受信任的憑證。 如需詳細資訊，請參閱 <<c0> [ 讓 web deploy 安全](#make-web-deploy-secure)。

1. 選擇**下一步**以顯示**摘要**畫面，然後選擇**發行**部署雲端服務。

    已發行的雲端服務。 建立虛擬機器已啟用 IIS，以便可以使用 Web Deploy 來更新 web 角色，而不需要重新發佈的遠端連線。

   > [!NOTE]
   > 如果您有多個 web 角色設定的執行個體時，會出現警告訊息，指出每個 web 角色，僅限於為了發佈您的應用程式所建立的封裝中的一個執行個體。 選取 **確定**以繼續。 需求 > 一節所述，您可以有多個 web 角色，但每個角色只有一個執行個體。

### <a name="update-your-web-role-by-using-web-deploy"></a>使用 Web Deploy 更新 web 角色

1. 若要使用 Web Deploy，請加入任何您想要發佈，然後以滑鼠右鍵按一下此方案中的專案節點，並指向的 Visual Studio 中 web 角色專案中進行程式碼變更**發佈**。 **發佈 Web**  對話方塊隨即出現。

1. （選擇性）如果您新增受信任的 SSL 憑證，以用於 IIS 的遠端連線時，您可以清除**允許不受信任的憑證**核取方塊。 如需如何將憑證新增至執行 Web Deploy 的安全資訊，請參閱下節**讓 Web Deploy 安全無**本文稍後。

1. 若要使用 Web Deploy，發佈機制需要的使用者名稱和您設定遠端桌面連線時，您首先發佈封裝的密碼。

   a. 在 **使用者名**，輸入使用者名稱。

   b. 在 **密碼**，輸入的密碼。

   c.  （選擇性）如果您想要將此密碼儲存在此設定檔中，選擇**儲存密碼**。

1. 若要將變更發行至 web 角色，選擇**發佈**。

    狀態列會顯示**發佈已開始**。 當發佈完成時，**發佈成功**隨即出現。 所做的變更現在已部署至您的虛擬機器上的 web 角色。 現在您可以開始您的 Azure 應用程式在 Azure 環境，以便測試您的變更。

### <a name="make-web-deploy-secure"></a>讓 web deploy 的安全

1. Web Deploy 使用不受信任、 自我簽署憑證根據預設，不建議用於上傳機密資料。 如果您需要保護機密資料進行此程序，您可以新增 SSL 憑證來用於 Web Deploy 連線。 此憑證必須受信任的憑證，您從憑證授權單位 (CA) 取得。

    若要讓 Web Deploy 安全每個虛擬機器的每個 web 角色，您必須上傳您想要使用適用於 web 的受信任的憑證部署至 Azure 入口網站。 此憑證可確保憑證會新增至您發佈您的應用程式時，會將 web 角色建立虛擬機器。

1. 若要加入 IIS 用來遠端連線的受信任的 SSL 憑證，請遵循下列步驟：

   a. 若要連接至虛擬機器正在執行 web 角色，選取 在 web 角色的執行個體**Cloud Explorer**或**伺服器總管**，然後選擇 **使用遠端桌面連線**命令。 如需如何連接至虛擬機器的詳細步驟，請參閱[使用 Visual Studio 的 Azure 雲端服務中的角色啟用遠端桌面連線](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio)。 您的瀏覽器會提示您下載`.rdp`檔案。

   b. 若要新增 SSL 憑證，請開啟管理服務在 IIS 管理員中。 在 IIS 管理員 中，開啟 啟用 SSL**繫結**連結**動作**窗格。 **新增網站繫結** 對話方塊隨即出現。 選擇**新增**，然後選擇 在 HTTPS**型別**下拉式清單。 在  **SSL 憑證**清單中，選擇您是否已透過 CA 簽署並上傳至 Azure 入口網站的 SSL 憑證。 如需詳細資訊，請參閱 <<c0> [ 設定管理服務的連線設定](http://go.microsoft.com/fwlink/?LinkId=215824)。

      > [!NOTE]
      > 如果您新增受信任的 SSL 憑證，在不會再出現黃色警告三角形**發行精靈**。

## <a name="include-files-in-the-service-package"></a>將檔案納入服務封裝

您可能需要特定的檔案納入服務封裝，以便它們可針對角色所建立的虛擬機器上。 例如，您可能想要新增`.exe`或`.msi`用啟動指令碼在服務封裝檔。 或者，您可能需要加入 web 角色或背景工作角色專案所需的組件。 若要包含的檔案，它們必須新增至 Azure 應用程式的方案。

1. 若要加入的服務封裝中的組件，請使用下列步驟：

   a. 在 [**方案總管] 中**，開啟遺漏所參考的組件之專案的專案節點。
   b. 將組件加入至專案，開啟捷徑功能表**參考**資料夾，然後選擇**加入參考**。 加入參考 對話方塊隨即出現。
   c.  選擇您想要新增，然後選擇 [參考]**確定**。 的參考新增至下方的清單**參考**資料夾。
   d. 開啟您所加入之組件的捷徑功能表，然後選擇**屬性**。 **屬性** 視窗隨即出現。

      若要納入服務封裝，此組件**複製到本機的清單**選擇 **，則為 True**。
1. 在 [**方案總管] 中**開啟遺漏所參考的組件之專案的專案節點。

1. 將組件加入至專案，開啟捷徑功能表**參考**資料夾，然後選擇**加入參考**。 **加入參考**對話方塊隨即出現。

1. 選擇您想要新增，然後選擇 參考**確定** 按鈕。

    的參考新增至下方的清單**參考**資料夾。

1. 開啟您所加入之組件的捷徑功能表，然後選擇**屬性**。 [屬性] 視窗隨即出現。

1. 若要納入服務封裝，此組件**複製到本機**清單中，選擇 **，則為 True**。

1. 若要將檔案納入服務封裝已加入至 web 角色專案中，開啟檔案的捷徑功能表，然後選擇 **屬性**。 從**屬性** 視窗中，選擇**內容**從**建置動作**清單方塊。

1. 若要將檔案納入服務封裝已加入至背景工作角色專案中，開啟檔案的捷徑功能表，然後選擇 **屬性**。 從**屬性** 視窗中，選擇**才複製**從**複製到輸出目錄**清單方塊。

## <a name="next-steps"></a>後續步驟

若要深入了解發行至 Azure 從 Visual Studio，請參閱[發佈 Azure 應用程式精靈](vs-azure-tools-publish-azure-application-wizard.md)。
