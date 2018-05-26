主控伺服器的 web Deploy 3.6 提供額外的組態功能，可從 UI 的發行設定檔案的建立。

1. 如果您有 Windows Server 上已安裝的 Web 部署 3.6，將它解除安裝使用**控制台** > **程式** > **解除安裝程式**.

1. 接下來，安裝 Web 部署 3.6 for Windows Server 上裝載的伺服器。

    若要安裝 Web Deploy 主控伺服器，使用[Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)。 (若要尋找 Web Platform Installer 連結從 IIS，請選取**IIS**伺服器管理員 的左窗格中。 以滑鼠右鍵按一下伺服器，然後選取**網際網路資訊服務 (IIS) 管理員**。)

    在 Web Platform Installer 中，您發現**主控伺服器的 Web Deploy**應用程式 索引標籤中。

1. 如果您沒有已安裝**IIS 管理指令碼及工具**，立即安裝。

    移至**選取伺服器角色** > **網頁伺服器 (IIS)** > **管理工具**，然後選取**IIS 管理指令碼和工具**角色中，按一下 **下一步**，然後再安裝角色。

    ![安裝 IIS 管理指令碼及工具](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    啟用的發行設定檔產生所需的指令碼及工具。

1. （選擇性）確認 Web Deploy 正在執行正確開啟**控制台 > 系統及安全性 > 系統管理工具 > 服務**並確定**Web Deployment Agent Service**執行 (服務名稱是在較舊的版本不同）。

    如果未執行的代理程式服務，請啟動它。 如果沒有完全，請移至**控制台 > 程式 > 解除安裝程式**，尋找**Microsoft Web Deploy <version>** 。 選擇**變更**安裝，並確定您選擇**將安裝至本機硬碟**Web Deploy 的元件。 完成變更安裝步驟。