
 
 
 
 
  public Form1()
 {
     InitializeComponent();
 }

     string NazevZ; // deklarace proměnné string pro název položky
     int AkStav;// deklarace proměnné int pro uložení hodnoty Aktulního stavu
     int MinZas;// deklarace proměnné int pro uložení hodnoty Minimálního stavu
     int Spotreba;// deklarace proměnné int pro uložení spotřeba/den
     int dny;// deklarace proměnné int pro uložení dní do dodávky
     double cenaK;// deklarace proměnné double pro uložení ceny za kus
     double VahaK;// deklarace proměnné double pro uložení vahy za kus
    


 private void Form1_Load(object sender, EventArgs e)
 {

 }

 private void textBox2_TextChanged(object sender, EventArgs e)


 
 {
     try

     
         {
         AkStav = Convert.ToInt32(textBox2.Text);

  
             if (AkStav <= 0) // podmínka, aby bylo možné do textboxu zapisovat pouze celé nezáporná čísla

      
             {
                 textBox2.Text = "";
             }

      
     }
     catch
         {
             textBox2.Text = "";
         }

     }
 
 
 
 

 try
     {
         if (textBox1.Text != "" && textBox2.Text != "" && textBox3.Text != "" && textBox4.Text != "" && textBox5.Text != "" && textBox6.Text != "" && textBox7.Text != "")
	 
			// kontrola, zda jsou všechny vstupní údaje vyplněny


   
         {
             int ObjednatK = (-1 * (AkStav - MinZas)) + (Spotreba * dny); // výpočet kusu na objednání
             if (ObjednatK < 0) // pokud by ObjednatK bylo menší než nula znamenáto že žádné další kusy nepotřebujem, proto zapišeme nulu

      
         {
                 ObjednatK = 0;
             }


					 textBox9.Text += NazevZ + " | Stav: " + AkStav.ToString()
						+ " | Min: " + MinZas.ToString()
						+ " | Spotřeba/den: " + Spotreba.ToString()
						+ " | Dny: " + dny.ToString()
						+ " | Cena/kus: " + cenaK.ToString() + " Kč"
						+ " | Váha/kus: " + VahaK.ToString() + " Kg"
						+ " | Objednat: " + ObjednatK.ToString() + " Ks"
						+ " | Celkem: " + (ObjednatK * cenaK).ToString() + " Kč"
						+ " | Váha: " + (ObjednatK * VahaK).ToString() + " Kg"
						+ Environment.NewLine;

				textBox1.Text = "";
             textBox2.Text = "";
             textBox3.Text = "";
             textBox4.Text = "";
             textBox5.Text = "";
             textBox6.Text = "";
             textBox7.Text = "";
         }
         else
         {
             MessageBox.Show("zkontroluj vstupní hodnoty");
         }
