# Sea-Of-Sharks-Version-1
Esta es la primera version del juego, la cual dejo de funcionar por el tema del procesador.
package application;
	
import javafx.application.Application;
import javafx.event.EventHandler;
import javafx.stage.Stage;
import javafx.scene.Group;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.image.Image;
import javafx.scene.image.ImageView;
import javafx.scene.layout.BorderPane;
import javafx.scene.text.Font;
import javafx.scene.text.FontPosture;
import javafx.scene.text.FontWeight;

public class Main extends Application {
	@Override
	public void start(Stage Stage) {
		Group root = new Group();
		Scene scene = new Scene(root,1460,775);

		Image fondo = new Image("PortadaInicio.jpg");
	    ImageView fndo= new ImageView();
		fndo.setImage(fondo);
		fndo.setFitWidth(1390);
		fndo.setFitHeight(730);

		Button botonStart = new Button("START");
		botonStart.setFont(Font.font("verdana",FontWeight.NORMAL, FontPosture.REGULAR,50));
		
		botonStart.setLayoutX(550);
		botonStart.setLayoutY(600);
		botonStart.setOnMouseClicked(new EventHandler<javafx.scene.input.MouseEvent>()
		{
			public void handle(javafx.scene.input.MouseEvent l)
			{
				Escenario escenario = new Escenario();
				escenario.CrearEscenario(Stage);
			}
		}
		);
		root.getChildren().addAll(fndo,botonStart);
		Stage.setScene(scene);
		Stage.show();
	}
	public static void main(String[] args) {
		launch(args);
	}
}

package application;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import javafx.event.EventHandler;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.ComboBox;
import javafx.scene.image.Image;
import javafx.scene.image.ImageView;
import javafx.scene.input.KeyCode;
import javafx.scene.layout.Pane;
import javafx.scene.text.Font;
import javafx.scene.text.FontPosture;
import javafx.scene.text.FontWeight;
import javafx.scene.text.Text;
import javafx.stage.Stage;

public class Escenario {
	Barco p1 = new Barco();
	double px1 = p1.PosicionBarcoX();
	double px2 = p1.PosicionBarcoY();
	Pane root = new Pane();

	public void CrearEscenario(Stage stage2)
	{
		Pane root = new Pane();
		Scene scene = new Scene(root,1390,7300);
		
		Image fondo = new Image("Mar.gif");
	    ImageView fndo= new ImageView();
	    fndo.setImage(fondo);
	    fndo.setFitWidth(1390);
	    fndo.setFitHeight(900);
	   
        Image hman=new Image("barc.gif");
		ImageView iv1 = new ImageView();
		iv1.setImage(hman);
		iv1.setFitWidth(100);
		iv1.setFitHeight(140);
		iv1.setTranslateX(px1);
		iv1.setTranslateY(px2);
		//iv1.setRotate(12);
		
		scene.setOnKeyPressed((event)-> {
            if (event.getCode() == KeyCode.RIGHT) {
                if(px1<=1260 ) {
                System.out.println("Derecha");
                px1=px1+10;
                iv1.setTranslateX(px1);}
            }
            if (event.getCode() == KeyCode.LEFT) {
            	System.out.println("Izquierda");
                if (px1 >= 10) {
                px1=px1-10;
                iv1.setTranslateX(px1);
                }
            }
            if (event.getCode() == KeyCode.UP) {
                if((px2)>=155) {	
                px2=px2-113;
                iv1.setTranslateY(px2);}
            }
            if (event.getCode() == KeyCode.DOWN) {
            	System.out.println("Abajo");
                if((px2)<=580) {
                px2=px2+113;
                iv1.setTranslateY(px2);}
            }
            root.getChildren().addAll(iv1);
		});
		Button botonSalir = new Button("SALIR");
		botonSalir.setFont(Font.font("verdana",FontWeight.NORMAL, FontPosture.REGULAR,20));
		botonSalir.setLayoutX(1250);
		botonSalir.setLayoutY(20);
		botonSalir.setOnMouseClicked(new EventHandler<javafx.scene.input.MouseEvent>()
		{
			public void handle(javafx.scene.input.MouseEvent l)
			{
			System.exit(0);
			}
		}
	);
	    root.getChildren().addAll(fndo,iv1,botonSalir);
	    stage2.setScene(scene);
		stage2.show();
	}
}

package application;

public class Barco {
double px1,px2;
	
	public Barco()
	{
	
	}
	public double PosicionBarcoX()
	{
		px1 =10;
		return px1;
	}
	
	public double PosicionBarcoY ()
	{
		px2 =84;
		return px2;
	}
}
