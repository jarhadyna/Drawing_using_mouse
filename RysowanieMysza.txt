import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import java.awt.event.MouseListener;

public class RysowanieMysza {
    public static void main(String[] args) {
        Okno okno=new Okno();
    }
}

class Okno extends JFrame  {
    public Okno(){
        setTitle("Rysowanie Mysz¹");
        setSize(400,400);
        Panel panel=new Panel();
        getContentPane().add(panel);
        setDefaultCloseOperation(3);
        setVisible(true);
    }
}

class Panel extends JPanel implements MouseListener {
    Point tab[]=new Point[80];
    int indeks=0;

    public Panel() { addMouseListener(this); }

    public void paintComponent(Graphics g) {
        g.clearRect(0,0,400,400);
        if(indeks>0){
            for (int i=0;i<indeks;i++) {
                if(i>0){
                    int xp=tab[i-1].x;
                    int yp=tab[i-1].y;
                    int xk=tab[i].x;
                    int yk=tab[i].y;
                    g.setColor(Color.red);
                    g.drawLine(xp, yp, xk, yk);
                }
                else g.drawLine(tab[i].x, tab[i].y, tab[i].x, tab[i].y);
            }
        }
    }


    public void mouseClicked(MouseEvent e) {
        int x=e.getX();
        int y=e.getY();
        tab[indeks]=new Point(x,y);
        indeks=indeks+1;
        this.repaint();
    }

    public void mouseEntered(MouseEvent e) {}
    public void mouseExited(MouseEvent e) {}
    public void mousePressed(MouseEvent e) {}
    public void mouseReleased(MouseEvent e) {}

}




