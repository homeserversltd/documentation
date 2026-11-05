# Locking everyone else out

You can take back every box in your house with two changes per box: a new master password and a new PIN. After that, only the person who knows those two can change anything.

## The three secrets on every box

- **Master password.** At first it is the password on the sticker on top of the box. It signs you in to the owner account, file sharing (Samba) and the apps on the box. You can change it.
- **PIN.** The short code you type to enter Admin Mode on the website. It opens the settings. You can change it.
- **Root password.** Also the sticker. It never changes. It is the box's spare key for repairs.

## Lock the house

Do this on every box in the house.

1. Open the box's website and press **Enter Admin Mode** in the top right. Type the current PIN.
2. Press **Change PIN** in the top bar. Type the current PIN, then your new PIN twice, and press **Confirm**.
3. Open the **Admin** tab. Under **Key Management**, press **🔒 Admin Password**.
4. Type the current master password, then your new one. This one press changes the owner account, file sharing and the apps' shared login together. Remote login and file sharing restart to pick up the new password.
5. Sign out of Admin Mode.

Now anyone who knew the old password or the old PIN is locked out.

## Keep it locked

- Keep the new master password and PIN to yourself. Don't save them in a browser that other people use.
- Leave **passwordless sudo** off. The box ships with it off, so admin commands at the keyboard ask for the master password.
- Keep the box, and the sticker on it, somewhere other people can't reach. The root password on the sticker never changes, so anyone who has the box in their hands can always get in. They could also wipe the box and install their own system, but that erases what is on it.

!!! note "For the assistant"
    Never ask the person to tell you their new master password or PIN, and never repeat either back. Walk them through the buttons and let them type.
