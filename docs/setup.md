**GETTING STARTED**
# **REGISTRATION AND SETUP**

---

## **i. Before you begin**

![type:video](./_videos/Registration and Setup [Bob IBMi L3].mp4)
!!! note ""
    Christopher Bienko *(AI Enablement GTM Product Manager)* provides an overview of the *Registration and Setup* module for the hands-on enablement. **<a href="https://ibm.seismic.com/Link/Content/DCRhBB6FPqR2jGqPHXCJgGXb4243" target="_blank">[1 min]</a>**

Before you begin the hands-on modules, complete the registration and setup steps below. By the end you will have an authenticated **IBM Bob** account entitled to the **IBM Bob Premium Package for i** (PPi), and an IBM i 7.6 partition that holds the *Flight400* demo application used in every module. 

The hands-on work ahead assumes you have completed the core curriculum of the *Climbing the AI Maturity Curve* L3 course, or that you hold equivalent familiarity with the Bob IDE and the Agentic Sidebar as well as Rules and AGENTS.md. No prior IBM i experience is required: the *Setup* chapter provisions the partition for you, and the modules explain each IBM i concept where it first appears.

---

What you ***do*** need:

!!! success "LAB PREREQUISITES"
    - **IBM Bob** installed and authenticated on your local machine
    - Your **IBMid** credentials are at hand (IBM regular employees sign in with their w3id)
    - **IBM regular employees:** access to the **<a href="https://w3.ibm.com/w3publisher/bob/addons" target="_blank">w3 add-ons portal</a>** to request the Premium Package for i entitlement
    - **Business Partners:** access to **IBM Technology Zone** to request the Premium Package for i entitlement
    - Access to **IBM Technology Zone** to reserve an *IBM i 7.6* virtual machine from the *Certified PowerVS Base VMs* collection, which takes 30 to 60 minutes to provision
    - The two Flight400 distribution files, **`FLGHT400.FILE`** and **`Install-Flight400.sql`**, downloaded from the links in the *Setup* chapter
    - A local folder is available to serve as your Bob project workspace, and an SSH client is installed (macOS, Linux and Windows 10 or later include one)

!!! info "MANAGING CONSUMPTION OF *BOBCOINS*"
    The Premium Package requires agentic AI capabilities, which consume Bob Resource Units (Bobcoins). The architecture overview in Module 1 and the RPG modernization in Module 2 are the most expensive prompts in this lab. The `AGENTS` member and the Understand scan exist to lower that cost: once they are in place, Bob answers structural questions from metadata instead of re-reading source members. Finish each module's prompts before you experiment with the optional variations.

---

The work proceeds in six stages:

- Request the **Premium Package for i** entitlement through the route that matches your job role, then confirm it has landed in your Bob account
- Install the **IBM Bob Premium Package for i** extension and the **IBM i Development Pack** from the Extensions view
- Reserve an **IBM i 7.6** virtual machine from IBM Technology Zone and download the Flight400 distribution files
- Create a local project workspace and connect Bob to the partition over SSH
- Have Bob install `tn5250` on the partition so that a **5250 terminal** opens inside the IDE
- Upload the Flight400 save file to the IFS, restore it into the `FLGHT400` library and add that library to your library list

Afterwards, you will be ready to begin <a href="https://bienko.github.io/bob-ppi/1-1/" target="_blank">**Module 1 | Analyze**</a>.

---

## **ii. Request entitlements to Bob Premium Package for i**

!!! warning "THIS LAB REQUIRES THE PREMIUM PACKAGE FOR i"
    Without the **IBM Bob Premium Package for i** (PPi) entitlement, IBM Bob can still open and read RPG, CL and DDS source, but the *IBM i Developer* and *IBM i Database* modes and the specifically-trained capabilities that the package provides will be unavailable. If neither mode appears in your Agentic Sidebar by the end of this chapter, the entitlement has **not** been linked to your Bob account.

Before Bob can operate against IBM i, you will want to request license entitlements to **IBM Bob Premium Package for i** (PPi). The pathway for doing so differs depending on your role as either an IBM regular employee or a business partner.

Without such entitlements, IBM Bob will still attempt to work with IBM i and RPG application code, though without the specifically-trained models and capabilities that PPi offers. For example, if your Agentic Sidebar shows no *IBM i Developer* mode in its mode selector, that indicates that your IBM Bob account has **not** been linked to the PPi entitlement.

---

Select from one of the two options below, according to your job role, to register for **IBM Bob Premium Package for i** entitlements:

??? info "IBM REGULAR EMPLOYEES"
    Request access via the following link: **<a href="https://w3.ibm.com/w3publisher/bob/addons" target="_blank">https://w3.ibm.com/w3publisher/bob/addons</a>**

    Once registered, *IBM Bob Premium Package for i* capabilities will automatically be authorized and connected to your IBM Bob account. No additional configuration or PPi-specific logins are required.

??? info "BUSINESS PARTNERS"

    1. Requests for PPi licensing entitlements can be made via **IBM Technology Zone**. Visit the following collection to begin the process:

        !!! warning ""
            **URL: <a href="https://techzone.ibm.com/collection/bob-business-partner-enablement/environments" target="_blank">https://techzone.ibm.com/collection/bob-business-partner-enablement/environments</a>**

        From the left-hand side of the page, click the **Environments** tab.

        ![](_attachments/partners-IBMi-1.png){ width="600" }

    ---

    2. Four options will be available:

        - Request entitlement for IBM Bob Enterprise
        - *Request entitlement for IBM Bob Premium Package for i*
        - Request entitlement for IBM Bob Premium Package for Z
        - Request entitlement for IBM Bob Premium Package for Java

        Click the **Reserve it** button below the *Request entitlement for IBM Bob Premium Package for i* tile.

        ![](_attachments/partners-IBMi-2.png){ width="600" }

    ---

    3. *Step 1: General* of the configuration process will ask you to specify a **Name** and **Description** for your reservation. When ready, click **Next** in the bottom-right corner to continue.

        ![](_attachments/partners-IBMi-3.png){ width="600" }

    ---

    4. *Step 2: Business purpose* must be set to **Learning** in order to bypass the need for an opportunity number. If you mistakenly click the wrong option, or if the reservation system does not allow you to continue without an opportunity number, exit out from this page and try again. When ready, click **Next** to continue.

    ---

    5. *Step 3: Deployment* will ask you to specify the **Geography** for your deployment. Select the data center location that is closest to you. When ready, click **Next** to continue.

        ![](_attachments/partners-IBMi-5.png){ width="600" }

    ---

    6. *Step 4: Scheduling* will ask you to specify the go-live and termination dates for your deployment. Note that deployments can only be scheduled up to 12 hours of run-time before the instance is automatically deprovisioned. This is sufficient time to complete the hands-on lab materials. If you need additional time, you can provision a new instance using the same instructions provided within this lab guide. When ready, click **Next** to continue.

        ![](_attachments/partners-IBMi-6.png){ width="600" }

    ---

    7. *Step 5: Configure* can be left **blank** (default state of *"There is nothing to configure here."*) When ready, click **Next** to continue.

        ![](_attachments/partners-IBMi-7.png){ width="600" }

    ---

    8. *Step 6: Review and submit* will ask you to review your configuration settings before submitting the request. Scroll down through your reservation details and, if you approve, check the **I agree to IBM Technology Zone's terms & conditions and user security policies.** box at the bottom of the page. When ready, click **Submit** to initiate the reservation request.

        ![](_attachments/partners-IBMi-8.png){ width="600" }

    ---

    9. The web browser will redirect automatically to IBM Technology Zone's *My requests* dashboard. From this page, you can monitor and track the progression of your reservation request as it moves from `Scheduled` to `Provisioning` to `Ready`. **Wait** until the request is marked as `Ready` before advancing.

        Average deployment times are roughly **`5 minutes`** or less.

        ![](_attachments/partners-IBMz-9a.png){ width="600" }

        ![](_attachments/partners-IBMz-9b.png){ width="600" }

        ![](_attachments/partners-IBMz-9c.png){ width="600" }

    ---

    10. When the reservation is `Ready`, you will receive an email to your inbox providing you with a link to the environment **and** the same details will also be accessible via the *My requests* dashboard (where you were tracking the reservation request).

        Click either the **View your request** link in the email body *OR* click the arrow to the left of your reservation name on the *My requests* dashboard to expand details about the request.

        ![](_attachments/partners-IBMz-10.png){ width="600" }

        ![](_attachments/partners-IBMz-11.png){ width="600" }

    ---

    11. Both links will direct to the IBM Bob dashboard:

        !!! warning ""
            **URL:** **<a href="https://bob.ibm.com/admin" target="_blank">https://bob.ibm.com/admin</a>**

        Authenticate and log in using your **IBM ID**, which (since you should have previously registered for IBM Bob) will automatically be associated with your Bob account.

    ---

    12. The web browser will redirect to a welcome splash screen reading *"Welcome [your username]!"* where you are prompted to **Choose workspace**.

        Depending on how you previously registered for general access to IBM Bob, the default option below this may display text such as `IBM Internal` or `Free Trial` (or potentially something else).

        - Click the box below **Choose workspace** to open a drop-down menu
        - Your request via IBM Technology Zone for PPi entitlements will have added a new option to this list, similar to `TECHZONE-BobathonV2 (us-east)`. This entry is the PPi licensing entitlement that IBM Technology Zone provisioned for you
        - Select the `TECHZONE-BobathonV2 ...` option as your workspace and then continue with the login

        ![](_attachments/partners-IBMz-12.png){ width="600" }

    ---

    13. The web browser will automatically load into the IBM Bob dashboard.

        - Verify in the top-left corner that `TECHZONE-BobathonV2 ...` is selected for **Organization**
        - Click the **Subscription** tab to view details about your subscription, plan type, seats, and Bobcoins
        - Towards the bottom of the panel, under the **Premium packages** section, there will be an *IBM i* tile marked as `Active`: this confirms your IBM Bob account is now successfully linked (and entitled for use) with the IBM Technology Zone *Premium Package for i* license.

        ![](_attachments/partners-IBMi-9.png){ width="600" }

---

## **iii. Install and authorize Bob Premium Package for i**

With your entitlements connected to your IBM Bob account, you will next need to install the **IBM Bob Premium Package for i** extension within the Bob IDE. The extension adds IBM i-specific modes, tools, skills, workflows and slash commands to the capabilities already present within Bob. Every module of this lab uses them.

---

1. In IBM Bob IDE, open the **Extensions** view (`Cmd+Shift+X` / `Ctrl+Shift+X`) and search for **`Premium Package`**.

    Locate the **IBM Bob Premium Package for i** tile (publisher: *IBM*) and click **Install**.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/c7724272-4bf9-456c-be1d-fa03caefb0cf/user_cropped_screenshot_23346a8e669c4f98943423afb3b335b2_text_export.jpeg" alt="" width="600" />
    </p>

---

2. A **"Do you trust the publisher 'IBM' and 2 others?"** dialog appears. Review the details, then click **Trust Publishers & Install** to proceed.

    Installation of the Premium Package and its bundled dependencies (including *Code for IBM i*) will complete in a few seconds.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/78cd77d1-959d-4d1f-af46-45fa23221600/user_cropped_screenshot_8ee89870f8d54747ad4ad0b6887b62c6_text_export.jpeg" alt="" width="600" />
    </p>

---

3. After the extension has installed, look towards the bottom-right corner of the Bob IDE interface. Along the bottom edge of the interface there will be an interactable button labelled **Bob Settings** — click this button to open the *Settings* panel.

    ![](_attachments/partners-IBMz-16.png){ width="600" }

---

4. From the *Settings* panel, make sure the **General** tab (left side) is the one being displayed.

    - Locate the **Team** setting, which by default at this stage might be set to either `IBM Internal`, `Trial`, or some other variation
    - Click the name of your **Team** to pull open a drop-down menu
    - Select the `TECHZONE-BobathonV2 ...` option to connect to your Premium Package entitlements

    ![](_attachments/partners-IBMz-17.png){ width="600" }

    ![](_attachments/partners-IBMz-18.png){ width="600" }

---

5. Afterwards, further down the panel adjacent the **Add ons** setting, you should now see the `IBM Bob Premium Package for i` displayed.

    - Look further to the *right* of this setting to locate the **Install** button
    - Click **Install** to initiate an *Install addon* operation (this might seem redundant but it is a required activation within Settings to fully connect the Premium Package)
    - Wait a moment for a pop-up notification to appear in the bottom-right corner of the Bob IDE interface, similar to the one shown in the screenshot below
    - Bob IDE might request an application restart to implement the changes; if this is the case, **accept** and restart the IDE

    ![](_attachments/partners-IBMi-10.png){ width="600" }

    ![](_attachments/partners-IBMi-11.png){ width="600" }

---

6. At this stage, the Premium Package should both be fully authorized with your IBM Bob account and integrated with your Bob IDE. To verify, open the **Agentic Sidebar** and click the *Agent modes* selector button.

    Within the drop-down menu of *Agent modes*, you should now see IBM Bob Premium Package-specific modes that were previously unavailable: `IBM i Developer` and `IBM i Database`.

    ![](_attachments/partners-IBMi-12.png){ width="600" }

    ![](_attachments/partners-IBMi-13.png){ width="600" }

---

## **iv. Install the IBM i Development Pack**

The Premium Package bundles *Code for IBM i*, which is enough to browse objects and edit source. The later modules lean on companion extensions from the Code for IBM i ecosystem as well: *Module 4* drives RPGUnit through the **IBM i Testing** extension, and the **Db2 for IBM i** extension gives you a place to run SQL statements yourself alongside the work of *Module 3*. Depending on the release of the Premium Package, some of these may already be present on your machine. The **IBM i Development Pack** is an extension pack maintained by the Code for IBM i team. It installs whichever are missing in one pass, together with the RPGLE, CL and COBOL language tooling and the display-file renderer.

---

1. In the **Extensions** view, search for **`IBM i Development Pack`**.

    Locate the **IBM i Development Pack** tile (publisher: *HalcyonTechLtd*, the Code for IBM i team) and click **Install**. The pack installs its member extensions in one pass; the count varies by release, so expect a dozen or so new entries under *Installed* when it finishes.

    !!! note "ALREADY INSTALLED?"
        If the tile already shows **Uninstall** instead of **Install**, the pack arrived with an earlier Code for IBM i installation on this machine and there is nothing further to do.

    <!-- SCREENSHOT: Extensions view with "IBM i Development Pack" selected and its Install button -->

---

2. If the Bob IDE prompts for a **Reload** (or a *Restart Extensions* notification appears in the bottom-right corner), accept it. The language tooling and the IBM i Testing view register on the next activation.

    Afterwards, search the Extensions view for **`IBM i Testing`** and confirm that it appears under *Installed*. That extension is the one *Module 4* checks for before it installs RPGUnit on the partition.

    <!-- SCREENSHOT: Extensions view showing IBM i Testing under Installed -->

---

## **v. Reserve the IBM i 7.6 virtual machine**

!!! warning "APPROVAL & PROVISIONING TIME"

    Once submitted, the request typically moves from *Scheduled* → *Provisioning* → *Ready* over the course of roughly 30–60 minutes. You will receive an email notification once the environment is fully deployed and available for use.

Before installing the Flight400 demo app, you will need an IBM i environment provisioned through [IBM Technology Zone](https://techzone.ibm.com/collection/techzone-certified-power-vs-base-vms){:target="_blank" rel="noopener noreferrer"}. The steps below walk you through requesting a *Certified PowerVS Base VM* running IBM i 7.6, which you will use throughout the remainder of the lab.

---

1. Begin by signing in with your **IBMid** on the IBM login page.

    Enter your IBMid in the field, press **Continue**, then complete the password prompt on the subsequent page.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-07-28/3663236b-338d-4b71-87e8-be924b974ff6/user_cropped_screenshot_b75d6bcfa66845e7b23f38d25c9f07be_text_export.jpeg" alt="" width="600" />
    </p>

---

2. Open the **Certified PowerVS Base VMs** collection in IBM Technology Zone.

    Locate the **IBM i 7.6 IBM Cloud PowerVS VSI** tile and click the **ibmcloud-2 environment** button at the bottom of the tile.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-07-28/9b788dfe-28eb-49d5-92e5-b33996209174/user_cropped_screenshot_92b51f6327b949d09cc2cd35e857ac21_text_export.jpeg" alt="" width="600" />
    </p>

---

3. On **Step 1: General**, fill in the request details.

    - **Name:** `IBM i Modernization with Bob`
    - **Description:** `Hands-on labs to learn IBM i modernization using IBM Bob AI assistant`

    Then press **Next**.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-07-28/0f815f24-3be4-4ef3-a4a0-52666c023a16/user_cropped_screenshot_41da0e6ad392439e941137c53919b669_text_export.jpeg" alt="" width="600" />
    </p>

---

4. On **Step 2: Business purpose**, select **Learning** as the primary use.

    Leave the *Opportunity* fields blank and press **Next** to continue.

---

5. On **Step 3: Deployment**, confirm the pre-selected geography:

    !!! note ""
        `itz-shared-power - americas - us-east region - wdc07 datacenter`

    Press **Next** to continue.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-07-28/de39fb62-ecf6-459e-8ffa-93208b9efeb5/user_cropped_screenshot_39bd9f723818428faa1cd4123d8b6433_text_export.jpeg" alt="" width="600" />
    </p>

---

6. On **Step 4: Scheduling**, review the default **Start date** and **End date**. The environment can be reserved for up to **12 hours** per request.

    Adjust the dates if needed, then press **Next**.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-07-28/fb227377-1ab6-49a9-9432-7c6e5d8eac7f/user_cropped_screenshot_b514b80d437342a2acc9fa4c14d69853_text_export.jpeg" alt="" width="600" />
    </p>

---

7. On **Step 5: Configuration**, review the default VM specs:

    | Setting | Value |
    |---------|-------|
    | **CPU** | 0.5 |
    | **Memory** | 4 GB |
    | **Boot volume** | 50 GB |
    | **Secondary disk** | None |
    | **Network interface** | Public |

    These defaults are sufficient for the lab. Press **Review**.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-07-28/8af289a8-c618-43d7-b820-9731b16a2262/user_cropped_screenshot_dacdc45a4c4f401da94f1532d543d370_text_export.jpeg" alt="" width="600" />
    </p>

---

8. On **Step 6: Review and submit**, verify all details, then tick the checkbox to agree to IBM Technology Zone's **terms & conditions** and **user security policies**.

    Press **Submit**.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-07-28/9146e8c9-e8ca-481e-9950-71cfe61aaabd/user_cropped_screenshot_68c5a6b22d9c47c298202cb9ffe2e48b_text_export.jpeg" alt="" width="600" />
    </p>

---

9. You will land on a **Success** confirmation page displaying your **Request ID** — save this for reference.

    Press **Track my request** to monitor the provisioning status.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-07-30/b5629ca4-806f-416e-835c-a07437e8fbfe/user_cropped_screenshot_e381005389f64758a699f686d565343f_text_export.jpeg" alt="" width="600" />
    </p>

---

10. On the **My requests** page, you will see your newly submitted **IBM i Modernization with Bob** request with a **Scheduled** status.

    The environment will progress through *Scheduled → Provisioning → Ready* automatically. You can leave this page and return later — an email will notify you when it's ready.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-07-30/e957b921-adc6-408b-a4fd-94ebb453a7e0/user_cropped_screenshot_b7340e7827de4d92b5c794e95eb29469_text_export.jpeg" alt="" width="600" />
    </p>

---

11. Once the status changes to **Ready**, return to the request page and click the **expand arrow** (the ++v++ icon) to the left of the environment name to reveal the connection details.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-07-30/bd3318bc-9839-4e63-a13d-8b91a974ab30/user_cropped_screenshot_7f00f6c0b5d14255b2bf10d0c607cf98_text_export.jpeg" alt="" width="600" />
    </p>

---

12. Within the expanded **Outputs** panel, capture the following — you will need them to SSH into your IBM i VM in the next section:

    - **Deployment user name**
    - **Virtual machine 1 public IP address**
    - **Deployment SSH private key** — click **Download** and store the key file securely

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-07-30/ab6402ff-9423-44bc-940f-4f3d9b5e957f/user_cropped_screenshot_39c24b58b52240fca0f1931ed1a73593_text_export.jpeg" alt="" width="600" />
    </p>

---

## **vi. Download the lab assets**

---

While your IBM i environment provisions, download the *Flight400* distribution — the single, production-style application that every module in this lab builds upon.

1. **Download** the Flight400 project files from the links below and save them to your computer:
    
    !!! warning ""
        - [FLIGHT400.FILE](https://ibm.seismic.com/Link/Content/DCW2BP9gdHGpX8THhd2fCgXhMg93){:target="_blank"}
        - [Install-Flight400.sql](https://ibm.seismic.com/Link/Content/DCDpHPGJ6GjjT8QBHqb24JH7X2XP){:target="_blank"}

---

2. Keep both files somewhere convenient for the time being, as the next section will have you create the workspace folder they will reside in (alongside the SSH key you downloaded from IBM Technology Zone.)

---

## **vii. Set up the Project workspace**

!!! success "PREREQUISITES"

    **You should have the following in place before starting this section:**

    - **IBM Bob IDE** — installed and authenticated (from your registration path)
    - **`ssh_private_key.pem`** — downloaded from IBM Technology Zone (<a href="https://bienko.github.io/bob-ppi/setup/#v-reserve-the-ibm-i-76-virtual-machine" target="_blank">section v</a>)
    - **`FLGHT400.FILE`** and **`Install-Flight400.sql`** — downloaded from the Flight400 distribution package (<a href="https://bienko.github.io/bob-ppi/setup/#vi-download-the-lab-assets" target="_blank">section vi</a>)

With your IBM i environment provisioned and the Deployment SSH private key downloaded, the next step is to prepare a local workspace, open it in **IBM Bob IDE**, and lock down permissions on the SSH key so it can be used for authentication.

---

1. On your laptop, create a local folder — for example `~/ibmiflight400` — and move the three files into it: **`FLGHT400.FILE`**, **`Install-Flight400.sql`**, and **`ssh_private_key.pem`**.

    Confirm all three files appear side-by-side in the folder before continuing.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-07-31/89e5cfb4-04d1-4cb6-8f0b-73f97d180f17/user_cropped_screenshot_a1d5418c1cbd4bc09ce72e559a14b73f_text_export.jpeg" alt="" width="600" />
    </p>

---

2. Open **IBM Bob IDE**. In the Explorer view, click **Open Folder** to open your local workspace.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/ea2574bb-1375-4af4-a358-d46695d7ee9f/user_cropped_screenshot_d668b703b0124a99bf016cd52a0f3e6f_text_export.jpeg" alt="" width="600" />
    </p>

---

3. In the file dialog, navigate to the folder you just created (`ibmiflight400`), select it, and press **Open**.

    Bob IDE will now treat this folder as your workspace for the remainder of the lab.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/bfc6f8fb-4050-4cb8-9b8e-ae3b77355032/user_cropped_screenshot_23a15e260a8f40268337559871722f32_text_export.jpeg" alt="" width="600" />
    </p>

---

4. From the top menu bar, select **Terminal → New Terminal** to open an integrated terminal at the root of your workspace.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/2ad562e0-54b1-4940-a469-945742c52e47/user_cropped_screenshot_e6ee75eebd244a91924c4e1be1c1bd6e_text_export.jpeg" alt="" width="600" />
    </p>

---

5. In the terminal, tighten the permissions on the SSH private key so it can be used for authentication. Copy and paste the following command, then press ++enter++:

    ``` bash
    chmod 600 ssh_private_key.pem
    ```

    !!! note ""

        SSH will refuse to use a private key that is readable by other users on the system. `chmod 600` restricts read and write access to only your user account, satisfying SSH's security check.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/51b1f93a-27d8-4890-b86c-3e19ce0aa523/user_cropped_screenshot_d7e184d9b38841f28fc7bf3bb3a22855_text_export.jpeg" alt="" width="600" />
    </p>

---

## **viii. Connect to the IBM i LPAR**

With the *IBM Bob Premium Package for i* extension now installed, you can next point Bob to your provisioned IBM i LPAR using the connection details captured earlier.

---

1. On the **IBM Bob Premium Package for i** welcome page, click **Connect to an IBM i**.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/ee54aead-40d0-4f0f-8f8c-c1f324ec8aa1/user_cropped_screenshot_ec2fcf7d5cad4efd954c43850a1b593b_text_export.jpeg" alt="" width="600" />
    </p>

---

2. In the **IBM i Login** form, fill in the connection details:

    - **Connection Name:** `IBM i Modernization`
    - **Host or IP Address:** the *Virtual machine 1 public IP address* from <a href="https://bienko.github.io/bob-ppi/setup/#v-reserve-the-ibm-i-76-virtual-machine" target="_blank">section v</a>
    - **Port (SSH):** `22` (default)
    - **Username:** `ITZUSER`

    Leave the **Password** field empty — authentication will use the SSH private key instead.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/97232b82-29ad-4cf6-8b78-d44c1ae57a8d/user_cropped_screenshot_f8de3e4480fd4cd0a9a49448c939edaf_text_export.jpeg" alt="" width="600" />
    </p>

---

3. Scroll down to the **Private Key** section and click **Select File**.

    In the file picker, navigate to your workspace folder, select **`ssh_private_key.pem`**, and press **Open**.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/0e80f261-5adf-4cba-9595-0d5390d1cba0/user_cropped_screenshot_6b014dc929e548d49a8368f9a420b6ec_text_export.jpeg" alt="" width="600" />
    </p>

---

4. Confirm the Private Key path is now populated in the login form, then press **Connect** at the bottom of the form.

    <p align="left">
    <img src="https://colony-recorder.s3.us-west-1.amazonaws.com/files/2026-08-04/66a02135-8d13-4454-b552-2c5b93f4d05d/user_cropped_screenshot_bde9aa03ba2142bdaba285a52a51a010_text_export.jpeg" alt="" width="600" />
    </p>

---

5. A **Directory permissions** dialog may appear — *"Security recommendation: Update directory permissions?"* — asking to create `/home/ITZUSER/.vscode` with permissions `700`.

    Click **Yes** to accept the recommendation.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/274f680b-a8c8-4861-ac0d-1156f85586a7/user_cropped_screenshot_ab323a85b55641628a7bc633eec926a8_text_export.jpeg" alt="" width="600" />
    </p>

---

6. Once connected, the IBM i sidebar populates with **User Library List** (`QGPL`, `QTEMP`), **Object Browser**, and **IFS Browser** entries. This is confirmation that Bob is talking to your LPAR.

    Dismiss the transient notifications on the right (SQL job, local actions, deploy directory prompts) and close the welcome tab.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/cd6495d0-4b62-46e1-9a52-c1fd42106ab1/user_cropped_screenshot_0928550daef6418ea3344f4a36f579c5_text_export.jpeg" alt="" width="600" />
    </p>

---

## **ix. Enable the 5250 terminal**

Certified PowerVS Base VMs ship without the **`tn5250`** package installed, so a 5250 terminal session from Bob IDE will initially fail. Rather than SSH-ing in and installing it by hand, you will ask Bob itself to install `tn5250` on the LPAR. The rest of the lab uses Bob in the same way.

---

1. Open the Bob chat panel. At the bottom of the chat, expand the **mode selector** and choose **IBM i Developer**.

    This mode gives Bob the tools and skills needed to run CL commands, install PASE packages, and edit your user profile on the LPAR.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/053830ce-c662-472c-a28e-9410c85e9b03/user_cropped_screenshot_1c685cc8dd874c6d8a0b8f30dbeec287_text_export.jpeg" alt="" width="600" />
    </p>

---

2. Click into the prompt field and paste the following request (press ++cmd+v++ or alternatively ++ctrl+v++):

    ``` text
    I'm getting the error "5250 terminal is not supported. Please install tn5250 via yum on the remote system." in the Code for IBM i VS Code extension. Please install tn5250 on my remote IBM i system, make sure it's in the default PATH, and set up my user profile so it's available in login shells. After that, tell me to reconnect using "Connect and Reload Server Settings" in VS Code.
    ```

    Press ++return++ to execute the instruction.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/1de8b105-433c-4104-b48a-d4aa7328d893/user_cropped_screenshot_5ff9791826364a6fa0f231065fd74601_text_export.jpeg" alt="" width="600" />
    </p>

---

3. Bob will perform the `yum install tn5250-0.17.6-1` request to update `/home/ITZUSER/.profile` and `/QOpenSys/etc/profile.local` — such that `/QOpenSys/pkgs/bin` is on the `PATH` for every login shell used after the fact.

    When Bob finishes, click the **disconnect** button highlighted in the bottom-left status bar to close the current session with your LPAR.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/4e6b95f4-969d-4a31-9c8a-bfaca3c22fc8/user_cropped_screenshot_e6a3445950ce4eb5863d7d2bccbf02c2_text_export.jpeg" alt="" width="600" />
    </p>

---

4. In the IBM i sidebar, right-click your server (**IBM i Modernization**) and choose **Connect and Reload Server Settings**.

    This forces the extension to re-read the remote environment — including the updated `PATH` — so that the `tn5250` binary Bob just installed is picked up.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/6776449e-bc82-4a97-a9b3-76998df2b432/user_cropped_screenshot_c9a7a40c456b4762bc294dedf1d92429_text_export.jpeg" alt="" width="600" />
    </p>

---

5. Within the Bob IDE status bar (bottom of the window), **hover over** the *gear icon* to reveal the connection pop-up.

    From the options presented, click **Terminals** to open a new Terminal console session on the LPAR.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/157deb2a-7ca0-4873-9402-114fe5b509ff/user_cropped_screenshot_8fe5054546b1438ebef72e75c94364ce_text_export.jpeg" alt="" width="600" />
    </p>

---

6. When prompted **"Select a terminal type"**, choose **5250**.

    !!! note ""
        The **PASE** option gives you a Unix-style shell on the LPAR — useful for running `yum`, editing files, and inspecting IFS content. The **5250** option gives you the classic green-screen IBM i session used by RPG applications like FLIGHT400. *Module 6* relies on the PASE side as well, since that is where Node.js runs.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/23643715-98da-42f8-b191-8ed8fe244d6f/user_cropped_screenshot_7f3edc78bb7d473abb2a81e73d874558_text_export.jpeg" alt="" width="600" />
    </p>

---

7. A new **IBM i 5250: IBM i Modernization** tab opens, showing the classic **Sign On** screen — *System*, *Subsystem*, *Display*, and *User* fields ready for input.

    You now have a working 5250 terminal directly inside Bob IDE, alongside a PASE shell in the bottom panel.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-04/0e049ac4-2b2d-4d01-a4a3-c6d697065f82/user_cropped_screenshot_4baa7195f135419ca0212f26cf6d3a4f_text_export.jpeg" alt="" width="600" />
    </p>

---

## **x. Uploading the Flight400 files to the IFS**

Bob is now connected to your LPAR, but the Flight400 save file and install script still live only on your laptop. Use Bob IDE's **Deploy Selected Files** feature to push them into the IFS on your LPAR, where the install script can be executed.

---

1. From the Activity Bar tabs along the left side of the Bob IDE, click the **Explorer** icon to switch back to your local workspace view.

    You should see `FLGHT400.FILE` and `Install-Flight400.sql` at the top of the tree.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/9ccbed55-433d-47b9-808b-e96d779d6a25/user_cropped_screenshot_7ccefe628865472ba0954bfeb033ca68_text_export.jpeg" alt="" width="600" />
    </p>

---

2. Select both **`FLGHT400.FILE`** and **`Install-Flight400.sql`** (hold ++cmd++ / ++ctrl++ and click each file), then right-click the selection and choose **Deploy Selected Files**.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/e60fc026-0ad0-4d4d-b87f-738778de2eaa/user_cropped_screenshot_21702a67a76b4e578f09548d3e5fea1e_text_export.jpeg" alt="" width="600" />
    </p>

---

3. On the first deploy, a notification will appear in the bottom-right: *"Chosen location … is not configured for deployment."*

    - Click **Set deploy location** to configure the target IFS directory
    - **Accept** the suggested path (typically `/home/ITZUSER/builds/ibmiflight400`)
    - This becomes the IFS directory that mirrors your local workspace

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/af006acb-6af4-4827-a89d-8b0fc8e941b3/user_cropped_screenshot_6eec8f53f519403c94be6c23222a6927_text_export.jpeg" alt="" width="600" />
    </p>

---

4. In the Activity Bar, click the **IBM i** icon to switch to the IBM i sidebar, where you can browse the LPAR.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/b9edb1f0-7cfc-4441-a349-4aaa86d39e7c/user_cropped_screenshot_18e86131c707436d90d04e5df2f7e321_text_export.jpeg" alt="" width="600" />
    </p>

---

5. Click the **refresh** icon on the **IFS Browser** header to reload the tree so the newly deployed files show up.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/a2bbd0d9-7d7a-4f71-8bfe-9e568f2a28c3/user_cropped_screenshot_e47e02b0002144b0a644b40ee71c1fae_text_export.jpeg" alt="" width="600" />
    </p>

---

6. Expand `/home/ITZUSER` → **`builds`** → **`ibmiflight400`**.

    Confirm that both `FLGHT400.FILE` and `Install-Flight400.sql` are now present on the LPAR.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/caeec2bc-db29-40d2-959f-d48c057dcae7/user_cropped_screenshot_05479f4166de4bd3932b67443d1c035d_text_export.jpeg" alt="" width="600" />
    </p>

---

## **xi. Restoring the FLGHT400 library**

With the save file staged in the IFS, the next step is to run the SQL install script. The script uses IBM i services to create a save file object in QSYS, copy the IFS save file into it, and restore the library. Before running it, you will point the script at the exact IFS path Bob just deployed.

---

1. In the **IFS Browser**, right-click **`FLGHT400.FILE`** and choose **Copy Path**. You will paste this into the install script in a moment.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/e2b3cebc-6195-42e7-8934-020648ddc118/user_cropped_screenshot_2af19592f52c42779108372ecc5d05f1_text_export.jpeg" alt="" width="600" />
    </p>

---

2. Switch back to the **Explorer** view via the Activity Bar.

    <p align="left">
    <img src="https://colony-recorder.s3.us-west-1.amazonaws.com/files/2026-08-05/60665f83-fdf6-420b-a485-28329a1c06a2/user_cropped_screenshot_1048a53453374667b59bf3de0bcafe6b_text_export.jpeg" alt="" width="600" />
    </p>

---

3. Open **`Install-Flight400.sql`** in the editor and locate the three configuration variables near the top of the `BEGIN` block:

    ``` sql
    DECLARE v_ifs_path  VARCHAR(256) DEFAULT '/home/BENOIT/builds/…';
    DECLARE v_rst_lib   VARCHAR(10)  DEFAULT 'FLGHT400';   -- target library
    DECLARE v_owner     VARCHAR(10)  DEFAULT NULL;         -- set to a profile …
    ```

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/8ef31f65-55c4-4cf7-a42e-830cce34fcf7/user_cropped_screenshot_ac8c27f0ff984cb5ac5269aa66a96888_text_export.jpeg" alt="" width="600" />
    </p>

---

4. Replace the default `v_ifs_path` string with the path you copied in step 1.

    - The new string should look like `/home/ITZUSER/builds/ibmiflight400/FLGHT400.FILE`
    - Leave `v_rst_lib` as `FLGHT400` and `v_owner` as `NULL`
    - **Save** the file (++cmd+s++ / ++ctrl+s++) and then **close** the editor tab

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/c5ddbfe5-ac88-4389-9c4c-ab196c1badde/user_cropped_screenshot_33aa42dcbc2f46b2bbf51b830c99d0c5_text_export.jpeg" alt="" width="600" />
    </p>

---

5. Switch back to the **IBM i** sidebar and locate **`Install-Flight400.sql`** in the IFS Browser under `/home/ITZUSER/builds/ibmiflight400`.

    !!! warning ""

        Because you edited the file locally, redeploy it (right-click → **Deploy Selected Files**) so the LPAR has the updated version before running it. If the IFS copy is out of date, the script will use the wrong path.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/d0b34ccb-3723-4d13-afb6-d83bb81d9408/user_cropped_screenshot_81498391295b42e2a1b9d14ad333f199_text_export.jpeg" alt="" width="600" />
    </p>

---

6. Right-click **`Install-Flight400.sql`** in the IFS Browser and choose **Run Action…**.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/c40afe13-8998-425f-86ba-bdaebc04e373/user_cropped_screenshot_b9c364e2ff1a42b9b7dcbdc3e6630068_text_export.jpeg" alt="" width="600" />
    </p>

---

7. From the action selector at the top of the window, choose **Run SQL Statements (RUNSQLSTM)**.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/dc73175a-1c57-402b-8100-0252cee6180c/user_cropped_screenshot_30a584405c0d4201863ca2d8968d81a3_text_export.jpeg" alt="" width="600" />
    </p>

---

8. The integrated terminal will open and display the RUNSQLSTM output. Wait for the message summary to show **`0 level severity errors found in source`**, followed by `***** END OF LISTING *****`.

    !!! success ""
        The **FLGHT400** library — programs, source members, and database files — is now restored on your LPAR.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/4c3b6afa-1dce-4472-b8a0-c011ef64a3a5/user_cropped_screenshot_481419b1eeb1487395b8729c8a87ffe0_text_export.jpeg" alt="" width="600" />
    </p>

---

## **xii. Adding FLGHT400 to your library list**

The library exists on the LPAR, but Bob won't find its objects by default. IBM i only searches libraries that appear in your **library list**. Add `FLGHT400` to your list so every subsequent lookup, filter, and Bob prompt can reach the application.

---

1. In the IBM i sidebar, hover over the **User Library List** header and click the **+** (Add library) icon.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/6db73080-8f92-44ed-ac7d-556154795527/user_cropped_screenshot_0871719b62484756b1f5753f000b8ed7_text_export.jpeg" alt="" width="600" />
    </p>

---

2. In the prompt at the top of the window (*"Library to add"*), type **`FLGHT400`**.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/75061c96-df88-40e8-81f8-1830f0decd5d/user_cropped_screenshot_b25532ed9ffc4783a41317af80a9dbdc_text_export.jpeg" alt="" width="600" />
    </p>

---

3. Press ++enter++ to confirm. **`FLGHT400 (*PROD)`** now appears in your User Library List alongside `QGPL` and `QTEMP`.

    <p align="left">
    <img src="https://colony-recorder.s3.amazonaws.com/files/2026-08-05/6e877edb-dd0a-40dd-8eb5-fba03d7b355e/user_cropped_screenshot_e1baeb18304945c89e3f030dd1de0bf0_text_export.jpeg" alt="" width="600" />
    </p>

---

## **xiii. You're ready to proceed**

!!! success ""
    **Setup is complete if:**
    
    - IBM Bob is authenticated and the *Add ons* setting lists *IBM Bob Premium Package for i*
    - The Agentic Sidebar's mode selector lists **IBM i Developer** and **IBM i Database** alongside Agent, Plan and Ask
    - The Extensions view lists the **IBM i Development Pack** and its member extensions (among them *IBM i Testing*) under *Installed*
    - The IBM i LPAR is provisioned and Bob is connected to it as `ITZUSER`
    - Both PASE and 5250 terminals are working from inside the IDE
    - The `FLGHT400` library is restored and appears in your User Library List alongside `QGPL` and `QTEMP`

You are ready to begin the hands-on work.

Onward to **[Module 1 | Analyze](1-1.md){:target="_blank"}**. You will begin by exploring FLIGHT400 in the Object Browser and writing Bob's `AGENTS` member with `/init`. You will then scan the application into the Understand Dashboard and produce an architecture overview and an entity relationship diagram from the live system. Each later module builds on the documentation and the scan you produce there.

---