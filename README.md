
 
 
 01
 
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








------------
02


	 int pondeli, utery, streda, ctvrtek, patek, sobota, nedele;
 int vyska, sirka;


 private void textBox4_TextChanged(object sender, EventArgs e)
 {
     try
     
     {
         ctvrtek = Convert.ToInt32(textBox4.Text);
         if (ctvrtek < 0 || ctvrtek > 100)
	 
         {
             MessageBox.Show("muzis zadat hodnotu mezi 0 az 100");
         }
	 
         panel1.Refresh();
     }
     
     catch { }
 }



   private void panel1_Paint(object sender, PaintEventArgs e)
 {

     vyska = panel1.Height;
     sirka = panel1.Width / 7;
     Graphics g = e.Graphics;
     Brush brush = new SolidBrush(Color.Red);
     Pen pen = new Pen(Color.IndianRed);

     int[] hodnoty = { pondeli, utery, streda, ctvrtek, patek, sobota, nedele };
     for (int i = 0; i < 7; i++)
     {
         int vyskaSloupce = (int)(vyska * (hodnoty[i] / 100.0));
         g.FillRectangle(brush, i * sirka + 5, vyska - vyskaSloupce, sirka - 10, vyskaSloupce);
     }


 }



---------
03




  public Form1()
  {
      InitializeComponent();
  }

  int vyskaPanelu = 400;
  
  int sirkaPanelu = 150;
  
  int aktualniVyska = 0;
  
  int krok = 0;
  
  int zmenaBarvyVyska = 0;
  


  private void panel1_Paint(object sender, PaintEventArgs e)
  {

  
      Graphics g = e.Graphics;

      // obrys sklenice
      
      g.DrawRectangle(Pens.Black, 10, 10, sirkaPanelu, vyskaPanelu);

      // výběr barvy podle výšky
      
      Brush barva = Brushes.Green;
      
      if (aktualniVyska >= zmenaBarvyVyska)
      
          barva = Brushes.Orange;

      g.FillRectangle(barva, 11, 10 + vyskaPanelu - aktualniVyska, sirkaPanelu - 1, aktualniVyska);
  }
  

 private void button1_Click(object sender, EventArgs e)
 {
     try
     {
         int objemSklenice = Convert.ToInt32(textBox1.Text);
	 
         int objemKapky = Convert.ToInt32(textBox2.Text);
	 
         int interval = Convert.ToInt32(textBox3.Text);
	 
         int procentaZmeny = Convert.ToInt32(textBox4.Text);

         krok = vyskaPanelu * objemKapky / objemSklenice;
	 
         zmenaBarvyVyska = vyskaPanelu * procentaZmeny / 100;

         timer1.Interval = interval;
	 
         timer1.Start();
     }
     
     catch
     
     {
         MessageBox.Show("Zadej všechna čísla správně.");
     }
 }

 private void timer1_Tick(object sender, EventArgs e)
 {

 
     if (aktualniVyska + krok <= vyskaPanelu)
     
     {
         aktualniVyska += krok;
	 
         Refresh();
     }
     
     else
     
     {
         timer1.Stop();
     }

     Refresh();
 }

 private void button2_Click(object sender, EventArgs e)
 
 {
     aktualniVyska = 0;
     
     timer1.Stop();
     
     Refresh();
 }
  
