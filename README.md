# Getoar
PieChart Project in Java, with the US Government Fiscal Year 1997 data in it.
Punimi Seminarik
Programim dhe Algoritma

Detyrë e jona për këtë seminar ka qenë shkrimi i një PieChart në java që i përmbushë këto
kërkesa të "Konsumatorit":


 


Duke ditur që është PieChart nënkupton se nevoitet pos metodës main edhe një metodë 
paintComponent si dhe 6 metoda për (maksimum) 6 slices që duhen vizatuar.




Së pari përbrenda konstruktorit të klasëssonë PieChartWriter kemi inicializuar 3 variabla që do na nevoiten në këtë program që janë:
 
Kështu pra do të inicializohen variablat nga "setSlice"në paintComponent ashtu që qdo slice të vizatohet në bazë të preferencës tonë.
Për të vizatuar PieChart kemi përdorur metodën "fillArc" të grafikut ashtu që qdo arc korrespondon me një slice të PieChart 
Këtu variabla "madhsia"përcakton hapjen e krahut dhe përdorimi i p.sh "madhsia1+madhsia2" na lejon që  slices ose arcs në këtë rast mos të viztohen mbi njera-tjetrën.
 
Që të gjitha slices të formojnë një rreth 360 shkallë është përdorur formula 
madhsia=amount*360/24
Në këtë rast është pjestuar me 24 sepse PieChart kjo duhej të paraqitte se si kalojmë 
ditën.Gjithashtu këtu kemi inicializuar vlerat color dhe sentence ashtu që të marrin vlern që ipet më vonë.
Së fundmi kemi një test class që përmbanë metodën main e cila lejon eksekutimin e programit me vlerat që  i japim seSlice(String label,int amount,Color ngjyra)
*Disa vlera dallojnë për detyrën nën (b) sepse nevoitej vizatimi i dy PieCharts por struktura është përafërsisht e njejtë 










Arkitektura










View- të jep një prezentim të modelit. View zakonisht merr gjendjen dhe të dhënat që I nevojiten për t’I shfaqur direkt nga modeli. View për ne është JFrame me metodat setSize, getContentPane, setVisible dhe setTitle dhe paintComponent me metodën Graphics g.	Controller- merr të hyrat nga përdoruesi duke i’a prezentuar modelit. Controlleri për ne është metoda main, sepse aty jepen të gjitha vlerat e dëshiruara që programi të ekzekutohet siç dëshirojmë.
	Model- modeli përmban të gjitha të dhënat, gjendejt dhe llogaritjet aritmetike. Modeli në rastin tonë është klasa PieChartWriter me metodat e saj prej setSlice1 deri në setSlice6. Ato përmbajnë të gjitha të dhënat, gjendjet dhe llogaritejt aritmetike të nevojshme që detyra të mos ketë gabime semantike.

                          







Mënyra alternative
Mënyra alternative e shkrimit të kodit të detyrës do të ishte shkrimi direkt i vlerave përkatëse në detyrë, d.m.th. inicializimi i vlerave në metodën paintComponent(Graphics g) duke e bërë të panevojshme nevojën e shkrimit të metodave setSlice. Pra kodi do të dukej kështu:
import java.awt.*;
import javax.swing.*;

public class USGovernmentFiscal1997 extends JPanel
 { public USGovernmentFiscal1997()
   { JFrame gov = new JFrame();
     gov.getContentPane().add(this);
     gov.setTitle("Fiscal Year 1997 of US");
     gov.setSize(900,600);
     gov.setVisible(true);
   }
   public void paintComponent(Graphics g)
   { g.setColor(Color.BLACK);
     g.fillArc(100, 100, 300, 300, 0, 46*36/10);
     g.drawString("INCOME:", 150, 50);
     g.drawString("personal income taxes: 46%", 100, 460);
     
     g.setColor(Color.RED);
     g.fillArc(100, 100, 300, 300, 46*36/10, 34*36/10);
     g.drawString("social security and medicare taxes: 34%", 100, 480);
     
     g.setColor(Color.CYAN);
     g.fillArc(100, 100, 300, 300, 46*36/10+34*36/10, 11/10*36);
     g.drawString("corporate income taxes: 11%", 100, 500);
     
     g.setColor(Color.WHITE);
     g.fillArc(100, 100, 300, 300, 46*36/10+34*36/10+11*36/10, 8/100*360);
     g.drawString("excise and customs taxes: 8%", 100, 520);
     
     g.setColor(Color.BLUE);
     g.fillArc(100, 100, 300, 300, 46*36/10+34*36/10+11*36/10+8*36/10, 360-(46*36/10+34*36/10+11*36/10+8*36/10));
     g.drawString("borrowing to cover deficit: 1%", 100, 540);
     
     g.setColor(Color.BLACK);
     g.fillArc(500, 100, 300, 300, 0, 38*36/10);
     g.drawString("OUTLAYS:", 550, 50);
     g.drawString("social security and medicare: 38%", 500, 450);
     
     g.setColor(Color.ORANGE);
     g.fillArc(500, 100, 300, 300, 38*36/10, 20*36/10);
     g.drawString("national defence: 20%", 500, 470);
     
     g.setColor(Color.BLUE);
     g.fillArc(500, 100, 300, 300, 38*36/10+20*36/10, 18*36/10);
     g.drawString("social programs: 18%", 500, 490);
     
     g.setColor(Color.MAGENTA);
     g.fillArc(500, 100, 300, 300, 38*36/10+20*36/10+18*36/10, 15*36/10);
     g.drawString("interest on national debt: 15%", 500, 510);
     
     g.setColor(Color.CYAN);
     g.fillArc(500, 100, 300, 300, 38*36/10+20*36/10+18*36/10+15*36/10, 7*36/10);
     g.drawString("human and community development: 7%", 500, 530);
     
     g.setColor(Color.RED);
     g.fillArc(500, 100, 300, 300, 38*36/10+20*36/10+18*36/10+15*36/10+7*36/10, 360-(38*36/10+20*36/10+18*36/10+15*36/10+7*36/10));
     g.drawString("general government: 2%", 500, 550);
     
     }
   public static void main(String[] args)
     {new USGovernmentFiscal1997();
     }
 }
Pra, kjo mënyrë e shkrimit në fillim mund të na duket më e lehtë por kur të na paraqitet nevoja për ndryshimin e vlerave të dhëna atëherë do ta shohim se kjo mënyrë do të na marrë shumë kohë dhe energji. Prandaj kjo mënyrë nuk është edhe shumë e preferueshme.
