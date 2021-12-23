# near-walletselector

# How to import package locally

- `npm install`
- `npm run build`
- `npm link`
- Go to folder where you want to import near-walletselector and type: `npm link near-walletselector`
- You can now import near-walletselector in your project for example like this: `import NearWalletSelector from "near-walletselector";`

# How to use

Import like this:

```
import NearWalletSelector from "near-walletselector";
```

Create near wallet instance:

```
const near = new NearWalletSelector({
    wallets: ["nearwallet", "senderwallet", "ledgerwallet"], // default wallets
    theme: "light" // light or dark
 });
```

Adding your custom wallet provider:

```
const near = new NearWalletSelector({
  wallets: ["nearwallet", "senderwallet", "ledgerwallet", "mywallet"], // <- add custom wallet name
  theme: "light",
  customWallets: {
    mywallet: {
      name: "My Wallet",
      icon: "https://via.placeholder.com/100x100",
      description: "My Wallet",
      onConnectFunction: () => {
        console.log("Connected to my wallet");
      },
      onDisconnectFunction: () => {
        console.log("Disconnected from my wallet");
      },
      isConnectedFunction: () => {
        return false;
      },
    },
  },
});
```

Show modal:

```
near.showModal();
```

Hide modal:

```
near.hideModal();
```

Is signed in:

```
near.wallets.isSignedIn();
```

Sign out:

```
near.wallets.signOut();
```

Get wallet information:

```
const wallet = near.wallets.getWallet("senderwallet");
wallet.getName();
wallet.getDescription();
wallet.getIcon();
```

Add event listeners to specific wallets:

```
near.wallets.getWallet("senderwallet").on("connect", (walletObj) => {
   // your code
});
```
