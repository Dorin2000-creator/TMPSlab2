1. Trebuie de instalat Live server
2. click ,,GO LIVE"

Design pattern-ul Singleton 
exportă o metodă numită getInstance, care verifică dacă o instanță Singleton există deja. Dacă nu există, se creează o instanță și se returnează. Funcția showMessage utilizează metoda getInstance pentru a obține instanța Singleton și afișează un mesaj.

Design pattern-ul Factory Method 
este implementat prin intermediul a două clase: Car și CarFactory. Clasa Car reprezintă un obiect mașină, iar clasa CarFactory este responsabilă pentru crearea acestor obiecte. Funcția createCar utilizează instanța carFactory pentru a crea un nou obiect Car și a afișa informații despre acesta.

Design pattern-ul Abstract Factory 
este implementat prin intermediul a trei clase: FordCar, BMWCar și CarAbstractFactory. Clasele FordCar și BMWCar reprezintă obiecte mașină specifice, iar clasa CarAbstractFactory este responsabilă pentru crearea acestor obiecte. Funcția createCar utilizează instanța carAbstractFactory pentru a crea un nou obiect mașină, în funcție de tipul selectat.

Design pattern-ul Builder 
este implementat prin intermediul clasei CarBuilder. Această clasă are o metodă de constructor care creează o instanță goală a obiectului Car. Această clasă are, de asemenea, metode pentru setarea valorilor modelului, anului și tipului mașinii și o metodă build care întoarce obiectul final. Funcția buildCar utilizează clasa CarBuilder pentru a construi un nou obiect Car, utilizând datele introduse de utilizator.