<h2 align="center">VMware Virtualization-Based System and Network Management Lab</h2>

<p>
-Bu proje, sanallaştırma teknolojileri kullanılarak bir sistemin kurulumu, yönetimi ve optimize edilmesi süreçlerini kapsamlı şekilde ele almak amacıyla hazırlanmıştır. Proje kapsamında bir sanal makine ortamı oluşturularak, sistem kaynaklarının verimli kullanımı, disk yönetimi, snapshot mekanizmaları, klonlama işlemleri ve sanal ağ yapılandırmaları gibi temel konular uygulamalı olarak gerçekleştirilmiştir. Ayrıca, farklı ağ türleri (NAT, Bridge, Host-Only) kullanılarak izolasyon ve erişim senaryoları test edilmiş, sistem taşınabilirliğini sağlamak adına export ve import işlemleri uygulanmıştır. Bu çalışma, gerçek dünya IT senaryolarına uygun şekilde, sistem yönetimi ve ağ yapılandırma becerilerini geliştirmeyi hedeflemektedir.
<br/><br/>
-This project was developed to comprehensively explore the setup, management, and optimization of systems using virtualization technologies. Within the scope of the project, a virtual machine environment was created, and key operations such as resource allocation, disk management, snapshot usage, cloning, and virtual network configuration were implemented in a practical manner. Additionally, different network types (NAT, Bridge, Host-Only) were configured to test isolation and accessibility scenarios. Export and import operations were also performed to ensure system portability. This project aims to simulate real-world IT scenarios and enhance skills in system administration and network configuration.
</p>

---

<h3>⚙️ Virtual Machine Settings / Sanal Makine Ayarları</h3>

<table>
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/1_virtual_machine_settings.png" width="100%" style="max-width:400px;" alt="VM Settings"/>
    </td>
    <td valign="top" width="50%">
      <p>
        <b>TR:</b> Sanal makinemde performans ve verimliliği dengelemek adına 4GB RAM ve 2 çekirdekli CPU yapılandırması tercih ettim. Depolama tarafında, fiziksel disk alanını optimize etmek için 50GB kapasiteli Dinamik Genişleyen disk yapısını kullandım. Ağ mimarisinde VMnet8 (NAT) modunu seçerek, makineyi dış ağ trafiğinden izole ettim; ihtiyaç duyulduğunda kontrollü servis erişimi sağlamak için port yönlendirme mantığını temel aldım.
      </p>
      <p>
        <b>EN:</b> To balance performance and resource efficiency, I allocated 4GB of RAM and 2 processor cores. For storage, I implemented a 50GB dynamically expanding disk to optimize physical space utilization. Network-wise, I configured the VM on VMnet8 (NAT) to ensure isolation, while keeping port forwarding as a secure strategy for controlled service access.
      </p>
    </td>
  </tr>
</table>

---

<h3>💾 Disk Adding And Expanding / Disk Ekleme Ve Genişletme</h3>

<table>
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/2_Disk_befor.png" width="100%" style="max-width:400px;" alt="Disk Before"/>
      <br/><sub><b>Before / Önce</b></sub>
    </td>
    <td align="center" width="50%">
      <img src="screenshots/3_Disk_after.png" width="100%" style="max-width:400px;" alt="Disk After"/>
      <br/><sub><b>After / Sonra</b></sub>
    </td>
  </tr>
  <tr>
    <td colspan="2">
      <p>
        <b>TR:</b> Projede sanal makine üzerinde disk genişletme ve yeni disk ekleme işlemleri gerçekleştirdim. İlk görselde diskin işlem yapılmadan önceki hali yer almaktadır. İkinci görselde ise mevcut diski 30 GB genişlettim. Bu işlemi yapma sebebim, disk alanının yetersiz kalması ve aynı disk üzerinde çalışmaya devam edecek olmamdı. Daha sonra sisteme 50 GB boyutunda yeni bir disk ekledim. Bu diski farklı verileri depolamak için kullanarak ana sistem diskinde oluşabilecek doluluk sorunlarının önüne geçmeyi hedefledim.
      </p>
      <p>
        <b>EN:</b> In this project, I performed disk extension and new disk addition operations on a virtual machine. In the first image, the disk is shown before any modifications. In the second image, I extended the existing disk by 30 GB due to insufficient storage space. Since I needed to continue working on the same disk, extending it was the most appropriate solution. After that, I added a new 50 GB disk to the system. I used this disk to store different types of data, aiming to prevent the main system disk from running out of space.
      </p>
    </td>
  </tr>
</table>

---

<h3>📸 Snapshots</h3>

<table>
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/4_snapshot1.png" width="100%" style="max-width:400px;" alt="Snapshot 1"/>
      <br/><sub><b>Stable State / Kararlı Durum</b></sub>
    </td>
    <td align="center" width="50%">
      <img src="screenshots/5_snapshot2.png" width="100%" style="max-width:400px;" alt="Snapshot 2"/>
      <br/><sub><b>Black Screen Error / Siyah Ekran Hatası</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/6_snapshot3.png" width="100%" style="max-width:400px;" alt="Snapshot 3"/>
      <br/><sub><b>Snapshot Manager</b></sub>
    </td>
    <td align="center" width="50%">
      <img src="screenshots/7_snapshot4.png" width="100%" style="max-width:400px;" alt="Snapshot 4"/>
      <br/><sub><b>Restored State / Geri Yükleme</b></sub>
    </td>
  </tr>
  <tr>
    <td colspan="2">
      <p>
        <b>TR:</b> Bu projede, sistemde yapılacak riskli işlemler öncesinde snapshot kullanımını test ettim. İlk görselde, herhangi bir işlem yapmadan önce sorunsuz ve stabil çalışan sistemin snapshot'unu aldım. Daha sonra sistem üzerinde şüpheli bir işlem gerçekleştirdim. İkinci görselde görüldüğü üzere bu işlem sonucunda sistemde siyah ekran hatası oluştu. Bu durum karşısında Snapshot Manager üzerinden daha önce aldığım snapshot'a geri dönerek sistemi kısa sürede eski, sorunsuz haline getirdim. Snapshot'lar, bu tür hatalı veya riskli işlemler sonrasında sistemi hızlıca geri yüklemek için oldukça etkili bir kurtarma yöntemidir. Ancak snapshot kullanımında zamanlama ve yönetimin doğru yapılması büyük önem taşır.
      </p>
      <p>
        <b>EN:</b> In this project, I tested the use of snapshots before performing risky operations on the system. In the first image, I took a snapshot of the system while it was running smoothly and in a stable state. After that, I performed a suspicious operation on the system. As shown in the second image, this resulted in a black screen error. To resolve this issue, I used the Snapshot Manager to revert the system back to the previously taken snapshot, restoring it to a stable state in a short time. Snapshots are a very effective recovery method for quickly restoring systems after faulty or risky operations. However, proper timing and management of snapshots are crucial for their effective use.
      </p>
    </td>
  </tr>
</table>

---

<h3>🔁 Virtual Machine Cloning / Sanal Makine Klonlama</h3>

<table>
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/8_virtual_machine_cloning1.png" width="100%" style="max-width:400px;" alt="Cloning Step 1"/>
      <br/><sub><b>Step 1 / Adım 1</b></sub>
    </td>
    <td align="center" width="50%">
      <img src="screenshots/9_virtual_machine_cloning2.png" width="100%" style="max-width:400px;" alt="Cloning Step 2"/>
      <br/><sub><b>Step 2 / Adım 2</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/10_virtual_machine_cloning3.png" width="100%" style="max-width:400px;" alt="Cloning Step 3"/>
      <br/><sub><b>Step 3 / Adım 3</b></sub>
    </td>
    <td align="center" width="50%">
      <img src="screenshots/11_virtual_machine_cloning4.png" width="100%" style="max-width:400px;" alt="Cloning Step 4"/>
      <br/><sub><b>Step 4 / Adım 4</b></sub>
    </td>
  </tr>
  <tr>
    <td colspan="2">
      <p>
        <b>TR:</b> Bu aşamada, kurduğum sanal makinenin klonunu oluşturdum. Bunun temel sebebi, aynı sistemi yeniden kurmanın zaman kaybı olmasıdır. Klonlama işlemi sayesinde mevcut sistemin birebir kopyasını alarak, bu kopya üzerinde istediğim işlemleri gerçekleştirebildim. Bu yöntem, hem zaman tasarrufu sağlar hem de ana sistemi riske atmadan test ve geliştirme yapma imkânı sunar.
      </p>
      <p>
        <b>EN:</b> At this stage, I created a clone of the virtual machine I had set up. The main reason for this was to avoid the time-consuming process of rebuilding the same system from scratch. By cloning the virtual machine, I was able to create an exact copy of the existing system and perform my desired operations on the cloned environment. This approach saves time and allows testing and development without risking the main system.
      </p>
    </td>
  </tr>
</table>

---

<h3>📦 Virtual Machine Export And Import / Sanal Makine Dışa ve İçeri Aktarma</h3>

<table>
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/12_virtual_machine_export1.png" width="100%" style="max-width:400px;" alt="Export Step 1"/>
      <br/><sub><b>Export - Step 1 / Dışa Aktarma - Adım 1</b></sub>
    </td>
    <td align="center" width="50%">
      <img src="screenshots/13_virtual_machine_export2.png" width="100%" style="max-width:400px;" alt="Export Step 2"/>
      <br/><sub><b>Export - Step 2 / Dışa Aktarma - Adım 2</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/14_virtual_machine_import1.png" width="100%" style="max-width:400px;" alt="Import Step 1"/>
      <br/><sub><b>Import - Step 1 / İçe Aktarma - Adım 1</b></sub>
    </td>
    <td align="center" width="50%">
      <img src="screenshots/15_virtual_machine_import2.png" width="100%" style="max-width:400px;" alt="Import Step 2"/>
      <br/><sub><b>Import - Step 2 / İçe Aktarma - Adım 2</b></sub>
    </td>
  </tr>
  <tr>
    <td colspan="2">
      <p>
        <b>TR:</b> Bu aşamada, ilk iki görselde export (dışa aktarma), son iki görselde ise import (içe aktarma) işlemlerini gerçekleştirdim. Export işlemini yapmamın amacı, oluşturduğum sanal makineyi farklı platformlara veya ortamlara kolayca taşıyabilmek ve kullanılabilir hale getirmektir. Bu sayede aynı sistemi yeniden kurmaya gerek kalmadan başka ortamlarda da çalıştırmak mümkün olmaktadır. Import işlemi ise export edilen sanal makinenin farklı bir platforma veya ortama yeniden kurulmasını sağlar. Bu yöntem, sistem taşınabilirliği ve hızlı kurulum açısından büyük avantaj sunar.
      </p>
      <p>
        <b>EN:</b> At this stage, I performed export operations in the first two images and import operations in the last two images. The purpose of the export process was to make the virtual machine portable across different platforms or environments and ensure it can be reused easily. This allows the same system to run in different environments without the need to rebuild it from scratch. The import process enables the exported virtual machine to be installed and run on another platform or environment. This approach provides significant advantages in terms of system portability and rapid deployment.
      </p>
    </td>
  </tr>
</table>

---

<h3>🌐 Virtualization Networks / Sanallaştırma Networkleri</h3>

<table>
  <tr>
    <td colspan="2">
      <p>
        <b>TR:</b> Sanallaştırma networkleri, sanal makinelerin (VM), host sistemlerin ve LAN yapılarının birbirleriyle iletişim kurmasını sağlamak için kullanılır. Farklı network türleri, farklı senaryolara göre erişim ve izolasyon seviyeleri sunar.<br/>
        <b>NAT:</b> Sanal makineler dış dünya ile iletişim kurabilir; dış sistemler VM'e doğrudan erişemez, port forwarding kullanılır.<br/>
        <b>Bridge:</b> VM fiziksel bir cihaz gibi ağa dahil olur, kendi IP adresini alarak doğrudan iletişim kurar.<br/>
        <b>Host-Only:</b> VM'ler yalnızca host makine ile birbirleri arasında iletişim kurabilir, dış ağa erişim yoktur.<br/>
        <b>Internal:</b> Yalnızca sanal makineler arasında iletişim; host veya dış ağlarla bağlantı yoktur.<br/>
        <b>Custom:</b> VMware üzerinde ihtiyaca göre özel ağ senaryoları oluşturulmasını sağlar.
      </p>
      <p>
        <b>EN:</b> Virtualization networks enable communication between virtual machines (VMs), host systems, and LAN environments.<br/>
        <b>NAT:</b> VMs can communicate externally but external systems cannot directly access VMs; port forwarding is used.<br/>
        <b>Bridge:</b> VM joins the physical network as an independent device and obtains its own IP address.<br/>
        <b>Host-Only:</b> VMs can only communicate with the host and each other, no external access.<br/>
        <b>Internal:</b> Communication only between VMs; no host or external network access.<br/>
        <b>Custom:</b> Create tailored network configurations based on specific requirements.
      </p>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/16_virtualization_networks1.png" width="100%" style="max-width:400px;" alt="Network Config 1"/>
      <br/><sub><b>Bridge Network</b></sub>
    </td>
    <td align="center" width="50%">
      <img src="screenshots/17_virtualization_networks2.png" width="100%" style="max-width:400px;" alt="Network Config 2"/>
      <br/><sub><b>NAT Network</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/18_virtualization_networks3.png" width="100%" style="max-width:400px;" alt="Network Config 3"/>
      <br/><sub><b>Host-Only Network</b></sub>
    </td>
    <td align="center" width="50%">
      <img src="screenshots/19_virtualization_networks4.png" width="100%" style="max-width:400px;" alt="Network Config 4"/>
      <br/><sub><b>Network Verification / Ağ Doğrulama</b></sub>
    </td>
  </tr>
  <tr>
    <td colspan="2">
      <p>
        <b>TR:</b> Bu aşamada farklı sanal makineler için farklı network türleri yapılandırdım. İlk Windows 11 sanal makinemi Bridge, klon makineyi NAT, import ettiğim makineyi ise Host-Only olarak ayarladım. Bridge olarak yapılandırdığım sanal makine, host sistemimin network'üne dahil oldu ve host ile aynı ağ yapısını kullanarak doğrudan iletişim kurabildi. Bu sayede host makineye ping atarak bağlantıyı doğruladım. NAT olarak ayarladığım sanal makine, VMware tarafından otomatik olarak atanan özel bir IP adresi aldı ve dış ağ ile NAT üzerinden iletişim kurabildi. Host-Only olarak yapılandırdığım sanal makine ise yalnızca host ve diğer sanal makineler arasında iletişim kurabilecek şekilde izole bir ağda çalışmaktadır.
      </p>
      <p>
        <b>EN:</b> At this stage, I configured different network types for different virtual machines. I set my first Windows 11 VM to Bridge, the cloned machine to NAT, and the imported machine to Host-Only. The Bridge VM became part of my host's network and communicated directly — verified by pinging the host. The NAT VM received a private IP from VMware and communicated with external networks through NAT. The Host-Only VM operates in an isolated network, communicating only with the host and other VMs, without external access.
      </p>
    </td>
  </tr>
</table>
