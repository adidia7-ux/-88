רוזן ענק הביטוח — מעקב הצעות יומי
מעקב יומי אחר הצעות מחיר מהמשווקים, עם רישום של איזו נציגה הוסיפה כל הצעה (כוכבה, מירי, אורנה, טל, עדי, רעות). כל יום מתחיל מאפס אוטומטית לפי שעון ישראל, והימים הקודמים נשמרים.
העלאה ל-GitHub Pages
ב-GitHub: New repository → שם כלשהו (למשל `rosen-tracker`) → Public → Create.
Add file → Upload files → מעלים את `index.html` (ואת הקובץ הזה) → Commit.
Settings → Pages → Source: `Deploy from a branch` → Branch: `main` / `(root)` → Save.
אחרי דקה-שתיים האתר יהיה זמין בכתובת `https://<שם-המשתמש>.github.io/rosen-tracker/`.
סנכרון בין כל המחשבים (Firebase — חינם)
בלי השלב הזה כל מחשב שומר את הנתונים רק אצלו.
נכנסים ל-https://console.firebase.google.com → Add project → נותנים שם → Create.
בתפריט: Build → Firestore Database → Create database → בוחרים מיקום (למשל `eur3`) → Start in production mode.
בלשונית Rules מדביקים ומפרסמים (Publish):
```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /{document=**} {
         allow read, write: if true;
       }
     }
   }
   ```
(הכללים האלה פתוחים לכל מי שיש לו את הקישור — מתאים לכלי פנימי פשוט.)
Project settings (גלגל השיניים) → Your apps → `</>` Web → נותנים שם → Register.
מעתיקים את ערכי `firebaseConfig` (apiKey, authDomain, projectId וכו').
ב-`index.html` מחפשים `window.FIREBASE_CONFIG` ומדביקים את הערכים בין המירכאות → שומרים ומעלים שוב ל-GitHub.
כשהכול מחובר, בראש הדף תופיע נקודה ירוקה: "מחובר — הנתונים מסונכרנים בזמן אמת".
