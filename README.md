# LG-Debrand-DS-Support-Velvet-5G(AT&T)

Full Credit:
https://xdaforums.com/t/tutorial-crossflash-bypass-opid-mismatched-error.4345963/


LG has made things difficult in flashing custom and even stock roms by this new OPID thing! It prevents us from crossflashing but we have been able to use TWRP and change the system and some other partitions to have a different rom. We had to make some changes into OP partition using HxD editor.
But now, through this tutorial, we're able to flash any rom without the need to change OPID in OP partition. Also, there is no need to root or unlock boot-loader.
I was successful to do this on some G8 (LMG820UM) but I AM NOT RESPONSIBLE FOR ANY HARM TO YOUR PHONE!

By continuing to read the following instructions you are actually accepting the risk.


IMPORTANT!
first, MAKE A FULL BACKUP OF ALL PARTITIONS; and I mean it!!!
at least, for your sake, make a backup of "modemst1, modemst2, fsg, fsc, ftm" partitions, for emergency.


Requirements
QPST and Qualcomm USB Driver (get)
LGE SM8150 Firehose (get)
LGUP 1.16.0.3 (get)
LGUP_Common.dll (get)
UI_Config.lgl (get)
LG Mobile Driver 4.4.2 (get)


Preparation
1. Install QPST and Qualcomm USB Driver.
2. Install LGUP.
3. Find the folder named "model" in the installation directory of LGUP, then Create a folder named "common" in the "model" folder.
4. Move "LGUP_Common.dll" and "UI_Config.lgl" into "common" folder. Change the attribute of "UI_Config.lgl" to read only.
5. Install LG Mobile Driver 4.4.2.


Steps
EDL-MOde:
1. Connect USB with PC & Phone
2. Power off the device pressing Vol+, Vol- and power button and when it turns off keep holding Vol- & power with constantly pressing Vol+
3. Phone will go into EDL mode without no screen(U will hear sound in PC)
4. For got Download Mode Keep Holding Vol+ while power on the device

A)
1. Open QFIL.
2. Change "Storage Type" to UFS.
3. Select "Flat Build".
4. Browse for "LGE SM8150 Firehose" and pick it.
5. Now, connect the phone to PC and boot into EDL mode.
6. Open "Select Port" and select the phone, press OK.
7. In "Tools" open the "Partition Manager".

B)
!!!BE CAREFUL TO DO EXACTLY AS THE INSTRUCTIONS SAY OR YOU WILL BRICK THE PHONE!!!
1. Make a backup of and erase these 7 partitions: **FTM, Modem_A, Modem_B, SID_A, SID_B, OP_A, OP_B.**
1.1. You have to left-click on a partition then right-click on it and select "Manage Partition Data".
1.2. In the pop-up window, you have 4 choices:
   I. Erase (to erase data on the partition),
   II. Read Data (to dump or back up the partition),
   III. Load Image (to restore the partition),
   IV. Close (to close the window).
1.3. First dump/back up the partition by choosing "Read Data" then Erase it.
3. Close the "Partition Manager" window.
4. Wait for 5 seconds then press Vol- and Power until it restarts.
3.1. Immediately after rebooting, Release the Vol- and Power buttons and press Vol+ to get into Download Mode.
Note: Do not let the phone to begin to boot! If it begins to boot, it may regenerate the SID and FTM partitions data and so you need to redo the whole step B.

C)
1. Open LGUP.
2. Pick your favorite KDZ.
3. Select "PARTITION DL".
4. Press Start. And a pop-up window will appear. In this window you can select which partitions to be flashed.
5. Here, uncheck these partitions: SID_A and SID_B. It will make it able to bypass the OPID Mismatched Error.
6. If you are in Sprint or other platforms you will get the message whether to change the model or not. Of course you know what to do =)

after completing the process it will boot up in some minutes and before starting the customization it will do one restart. just be patient.


ERRORS, QUESTIONS, TROUBLESHOOTING
1. Can I crossflash V50, V60, G8X or other LG devices using this method?
I did it on V50. Maybe it'll work on your devices maybe won't. There's one way to find out; make backup and give it a try.
2. SN is gone, zero, etc.
Restore your original FTM.
3. I can't get into recovery.
Restore the original FTM.
4. I got NT-Code error.
It's been discussed many times in the thread and some solutions have been presented (such as this one, thanks to @animo214 and this, thanks to @kt-Froggy as well as this one, thanks to @StvOchi ). However, you can ignore it if the phone got network.
Note: You need to disable verity on the phone in advance otherwise changes in cust_path_mapping.cfg won't be saved.
5. IMEI is lost, zero, null etc.
Restore LUN5 partitions. If you have no backup it should be repaired using Octopus box. Go to 16.
6. I got "permanently locked" error.
This is because of IMPL lock and you have to restore LUN5 partitions. In case of having no backup you should use Octopus box.
7. All partitions are deleted accidentally.
Follow this instructions.
8. I need to get into PDM mode.
Unzip and restore the attached PDM to FTM partition. Remember, you need to restore your FTM to get into OS.
9. Can I use another phone's LUN5 backup?
NO.
10. Can I use another phone's FTM backup?
Yes. All partitions can be restored from another phone's backup except LUN5 partitions.
11. My phone is stuck in boot-loop.
Restore the original FTM and if it doesn't help redo the whole crossflash process and use a different KDZ this time.
12. Which KDZ is the best (for any matter of use)?
I do not know.
13. Can I crossflash from any source variant to Korean variant or vice versa?
Yes it is possible but you may get error on opening stock camera application because of hardware differences. There are some methods to solve the issue which you can search and find them.
14. Can I downgrade using this method?
Yes.
15. I erased partitions (ftm, op_a, op_b, modem_a, modem_b, sid_a, sid_b) but it still does not let me to crossflash.
Redo the whole process and this time make backup of and erase these partitions too, on both sides A and B: vendor, product, system, boot and userdata. Do not make backup of userdata partition.
16. How can I write IMEI?
A) Dump modem_a and create a copy of it. Then open it in UltraISO and remove IMEIPROT files from image folder. Save and restore it in place of modem_a and modem_b partitions.
B) Make backup of FTM and then flash or restore the PDM file (attached) into your ftm partition. Restart the phone; you'll get into PDM mode.
C) Open Tutty (attached). Select "Serial" in protocol and the proper port of your phone's modem driver. Click open. To test if you have selected the proper port number type "at" and hit enter it should respond"ok". Type the code at%imei=# (replace # with your IMEI) and hit enter. It doesn't matter you get "error" or "ok" after that, just check if IMEI is written via this code at%imei=?. If IMEI is written so you'll have the right MEID and ESN too.
D) Restore the original ftm and modem_a in place of modem_a and modem_b. Restart the phone.
I've already tested this method on V30, V50 and G8. Remember, if the phone has IMPL lock it'll throw "perm. locked" error even if you have written the IMEI.
17. I have lost GPT files of my LG G8, G8X, G8S, V50, etc. and Qfil partition manager does not show anything in the list.
You need to flash GPT files to your device with fh_loader (see this, part C). For that matter use KDZ_Tools to Extract DZ from a KDZ of your device. Then extract the DZ using -c at the end of extracting command. For example: unkdz -f FILE_NAME.kdz -c. It will extract all files besides all GPTs.
18. Which are the LUN5 partitions?
SM8150 has 7 physical partitions known as LUNs which are numbered from 0 to 6. Each LUN is split into several partitions. In Qfil Partition Manager you can see all partitions except those of LUN3 and LUN6 which are hidden. The number of LUNs are shown under the first column named LUN. Therefore, all partitions in front of number 5 are LUN5 partitions.
