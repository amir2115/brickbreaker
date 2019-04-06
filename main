import javafx.animation.KeyFrame;
import javafx.animation.Timeline;
import javafx.application.Application;
import javafx.event.ActionEvent;
import javafx.event.EventHandler;
import javafx.geometry.Bounds;
import javafx.geometry.Pos;
import javafx.scene.Group;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.input.KeyEvent;
import javafx.scene.layout.*;
import javafx.scene.paint.Color;
import javafx.scene.shape.*;
import javafx.stage.Stage;
import javafx.util.Duration;

import java.util.Timer;
import java.util.TimerTask;

public class Main3 extends Application {
    //method for move the bar
    private void moveCircleOnKeyPress(Scene gamescene,Rectangle bar) {
        gamescene.setOnKeyPressed(new EventHandler<KeyEvent>() {
            @Override public void handle(KeyEvent event) {
                data d = new data();
                switch (event.getCode()) {
                    case RIGHT: bar.setX(bar.getX() + d.barspeed); break;
                    case LEFT:  bar.setX(bar.getX() - d.barspeed); break;
                }
            }
        });
    }
    @Override
    public void start(Stage primaryStage) throws Exception{
        data d = new data();
        Group root = new Group();
        VBox layoutMenu= new VBox(10);
        layoutMenu.setPrefWidth(100);
        Label Score = new Label();
        Score.setText("Score: ");
        Score.setLayoutX(720);
        Score.setLayoutY(5);
        Group groupA = new Group();


        VBox difficult= new VBox(10);
        difficult.setPrefWidth(100);
        //Declaring scenes
        Scene menu = new Scene(layoutMenu,data.Width,data.Height);
        Scene gamescene = new Scene(root,data.Width,data.Height);
        Scene gamedifficulty = new Scene(difficult,data.Width,data.Height);


        //Creating Buttons
        Button playGameButton= new Button("Play Game");
        Button scoresButton = new Button("difficulty");
        Button exitButton = new Button("Exit");
        Button menuButton = new Button("Menu");
        Button level1= new Button("level1");
        Button level2 = new Button("level2");
        Button level3 = new Button("level3");
        Button level4 = new Button("level4");
        Button level5 = new Button("level5");
        //Creating Ball
        Circle ball = circle.createball();
        //Creating Bar
        Rectangle bar = new Rectangle(data.Width / 2 - (d.barx / 2),data.Height - d.bary, d.barx, d.bary);
        bar.setArcHeight(10);
        bar.setArcWidth(10);
        bar.setFill(Color.BLACK);

        groupA.getChildren().addAll(bar);
        root.getChildren().addAll(ball, groupA);
        root.getChildren().add(createBoundsRectangle(ball.getBoundsInParent()));
        root.getChildren().add(createBoundsRectangle(bar.getBoundsInParent()));

        // Adding items to the layoutMenu and gameMenu and gamescene
        layoutMenu.getChildren().addAll(playGameButton,scoresButton,exitButton);
        root.getChildren().addAll(menuButton,Score);

        layoutMenu.setAlignment(Pos.CENTER);
        playGameButton.setMinWidth(layoutMenu.getPrefWidth());
        scoresButton.setMinWidth(layoutMenu.getPrefWidth());
        exitButton.setMinWidth(layoutMenu.getPrefWidth());

        //Align buttons and bar
        difficult.setAlignment(Pos.CENTER);
        playGameButton.setMinWidth(difficult.getPrefWidth());
        scoresButton.setMinWidth(difficult.getPrefWidth());
        exitButton.setMinWidth(difficult.getPrefWidth());
        difficult.getChildren().addAll(level1,level2,level3,level4,level5);

        //Events of buttons
        playGameButton.setOnAction(new EventHandler<ActionEvent>() {
            @Override
            public void handle(ActionEvent event) {
                Rectangle[] b = new Rectangle[brick.briksrows * brick.brikscolumns];
                Label[] labels = new Label[brick.briksrows * brick.brikscolumns];
                createbricks(b, labels, groupA, root);
                timeloop(ball, d, b, groupA, labels, bar);
//                primaryStage.setWidth(data.Width);
//                primaryStage.setHeight(data.Height);
                primaryStage.setScene(gamescene);
            }
        });
        scoresButton.setOnAction(e -> primaryStage.setScene(gamedifficulty));
        menuButton.setOnAction(e -> primaryStage.setScene(menu));
        level1.setOnAction(new EventHandler<ActionEvent>() {
            @Override
            public void handle(ActionEvent event) {
                d.GAMESPEED = 9.65;
                d.barspeed = 50;
//                data.Height = 680;
//                brick.brikscolumns = 20;
                primaryStage.setScene(menu);
            }
        });
        level2.setOnAction(new EventHandler<ActionEvent>() {
            @Override
            public void handle(ActionEvent event) {
                d.GAMESPEED = 9.85;
                d.barspeed = 45;
                data.Height = 580;
                brick.brikscolumns = 19;
                primaryStage.setScene(menu);
            }
        });
        level3.setOnAction(new EventHandler<ActionEvent>() {
            @Override
            public void handle(ActionEvent event) {
                d.GAMESPEED = 10.05;
                d.barspeed = 40;
                data.Height = 480;
                brick.brikscolumns = 18;
                primaryStage.setScene(menu);
            }
        });
        level4.setOnAction(new EventHandler<ActionEvent>() {
            @Override
            public void handle(ActionEvent event) {
                d.GAMESPEED = 10.25;
                d.barspeed = 35;
                data.Height = 430;
                brick.brikscolumns = 17;
                primaryStage.setScene(menu);
            }
        });
        level5.setOnAction(new EventHandler<ActionEvent>() {
            @Override
            public void handle(ActionEvent event) {
                d.GAMESPEED = 10.35;
                d.barspeed = 30;
                data.Height = 380;
                brick.brikscolumns = 16;
                primaryStage.setScene(menu);
            }
        });
        layoutMenu.setStyle("-fx-background-color: #2C3539;");
        difficult.setStyle("-fx-background-color: #2C3539;");
        primaryStage.setTitle("Amirproject");
        primaryStage.setScene(menu);

        moveCircleOnKeyPress(gamescene, bar);
        primaryStage.show();

    }
    public void createbricks(Rectangle[] b, Label[] labels, Group groupA, Group root){
        int i, x , y;
        for(int j = 0; j < brick.briksrows; j++){
            y = brick.bricksy + (j * (brick.bricksy + brick.bricksmargin));
            for(i = brick.brikscolumns * j, x = 0; x <= data.Width - brick.bricksx; x += brick.bricksx + brick.bricksmargin, i++ ){
                b[i] = brick.createbrick(x, y , j);
                labels[i] = brick.createlable(x, y);
                groupA.getChildren().addAll(b[i],labels[i]);
                root.getChildren().add(createBoundsRectangle(b[i].getBoundsInParent()));
            }
        }
    }
    public void timeloop (Circle ball, data d, Rectangle[] b, Group groupA,Label[] labels,Rectangle bar){
        final Timeline loop = new Timeline(new KeyFrame(Duration.millis(d.GAMESPEED), new EventHandler<ActionEvent>() {
            int ballposition = 0;
            @Override
            public void handle(final ActionEvent t) {
                ball.setLayoutX(ball.getLayoutX() + circle.dx);
                ball.setLayoutY(ball.getLayoutY() + circle.dy);

                //Collision for walls
                final boolean atRightBorder = ball.getLayoutX() >= (data.Width - circle.radius);
                final boolean atLeftBorder = ball.getLayoutX() <= (circle.radius);
                final boolean atBottomBorder = ball.getLayoutY() >= (data.Height - circle.radius);
                final boolean atTopBorder = ball.getLayoutY() <= (circle.radius + d.aligntoppage);

                if (atRightBorder || atLeftBorder) {
                    circle.dx *= -1;
                }
                if (atBottomBorder || atTopBorder) {
                    circle.dy *= -1;
                }
//                if(atBottomBorder) System.out.println("end");

                //Collision for brick bar
//                if(ball.getBoundsInParent().intersects(bar.getLayoutBounds())){
////                    Shape intersect = Shape.intersect(ball, bar);
////                    if(intersect.getBoundsInLocal().getWidth() != -1){
////                        // Collision handling here
////                    }
//                    dy*=-1;
//                }
//                double a = ball.getLayoutX();
//                double c = ball.getCenterY();
                double a = 0, c = 0;
                for(int i = 0;i < brick.brikscolumns * brick.briksrows;i++){
                    if(groupA.getChildren().contains(b[i]) && Integer.valueOf(labels[i].getText()) >= 0){
                        if(((Path)Shape.intersect(ball, b[i])).getElements().size() > 0){
                            System.out.println("brickx =  " + b[i].getX() + " bricky =  " + b[i].getY() + " ballx =  " + ball.getLayoutX() + " bally =  " + ball.getLayoutY() + " tashkhis =  " + rectanglevajh(ball.getLayoutX(), ball.getLayoutY() ,b[i],brick.bricksx));
//                            System.out.println(rectanglevajh(a, c ,b[i],brick.bricksx));
//                            if(rectanglevajh(ball.getLayoutX(), ball.getLayoutY() ,b[i], brick.bricksx) == 2 || rectanglevajh(ball.getLayoutX(), ball.getLayoutY() ,b[i], brick.bricksx) == 4){
//                                circle.dx*=-1;
////                                System.out.println(1);
//                            }
                            if(b[i].getX() == a && b[i].getY() == c){
                                circle.dx*=-1;
                            }
                            else {
                                circle.dy = circle.dy * circle.dy / Math.abs(circle.dy);
//                                System.out.println(2);
                            }
                            brick.inttocolor(Integer.valueOf(labels[i].getText()));
                            b[i].setFill(Color.rgb(brick.r,brick.g,brick.b));
                            labels[i].setText(String.valueOf(Integer.valueOf(labels[i].getText()) - 1));
//                            if(i == 43){
//                                circle.speedreward();
////                                circle.speedrefresh();
//                            }
                            if(Integer.valueOf(labels[i].getText()) == 0){
                                labels[i].setText("");
                                groupA.getChildren().remove(b[i]);
                            }
                        }
                        a = b[i].getX();
                        c = b[i].getY();
                    }
                }
                double markdxball = circle.dx / Math.abs(circle.dx);
                if (((Path)Shape.intersect(ball, bar)).getElements().size() > 0) {
                    if(markdxball > 0){
                        double d2 = bar.getWidth();
                        double d1 = ball.getLayoutX() - bar.getX();
                        double arc = (120 * (d1 / d2)) + 30;
                        double kt2 = Math.pow(Math.tan(arc), 2);
                        double K = Math.sqrt(circle.ballduration / (kt2 + 1));
                        circle.dy = -1 * K * Math.abs(Math.tan(arc));
                        if(arc < 90) circle.dx = -1 * K;
                        if(arc > 90) circle.dx = K;
                        if(arc == 90) circle.dx = 0;
//                        System.out.println("1       " + arc + " dx = " + circle.dx);
                    }else if (markdxball < 0){
                        double d2 = bar.getWidth();
                        double d1 = d2 + bar.getX() - ball.getLayoutX();
                        double arc = (120 * (d1 / d2)) + 30;
                        double kt2 = Math.pow(Math.tan(arc), 2);
                        double K = Math.sqrt(circle.ballduration / (kt2 + 1));
                        circle.dy = -1 * K * Math.abs(Math.tan(arc));
                        if(arc < 90) circle.dx = K;
                        if(arc > 90) circle.dx = -1 * K;
                        if(arc == 90) circle.dx = 0;
//                        System.out.println("2       " + arc + " dx = " + circle.dx);
                    }
//                    d.dy*=-1;
                }
                //Bar must stay in scene
                final boolean atRight = bar.getX() >= (data.Width - d.barx);
                final boolean atLeft = bar.getX() <= (0);
//                System.out.println("ball : " + ball.getLayoutX());
                if(atRight){
                    bar.setX(data.Width - d.barx);
                }
                else if(atLeft){
                    bar.setX(0);
                }
            }
        }));
        loop.setCycleCount(Timeline.INDEFINITE);
        loop.play();
    }
    private Rectangle createBoundsRectangle(Bounds bounds) {
        Rectangle rect = new Rectangle();
        rect.setFill(Color.TRANSPARENT);
        rect.setStrokeWidth(3);
        rect.setX(bounds.getMinX());
        rect.setY(bounds.getMinY());
        rect.setWidth(bounds.getWidth());
        rect.setHeight(bounds.getHeight());
        return rect;
    }
    public int rectanglevajh (double ballx, double bally, Rectangle brick, int recwidth){
        if(ballx + circle.radius >= brick.getX() && ballx - circle.radius <= (brick.getX() + recwidth)){
            if (bally - brick.getY() < circle.radius){
                if(ballx < brick.getX()) return 4;
                else if(ballx > (brick.getX() + recwidth)) return 2;
            }
            if (bally > brick.getY()) return 3;
            else if (bally < brick.getY()) return 1;
        }else if(ballx < brick.getX()) return 4;
        else if(ballx > (brick.getX() + recwidth)) return 2;
        return 0;
    }
    public static void main(String[] args) {
        launch(args);
    }
}
//    brickx =  318.0 bricky =  96.0 ballx =  375.7679047003153 bally =  115.6889577876781
//    brickx =  318.0 bricky =  96.0 ballx =  372.3404055268057 bally =  118.18940763032464
//    brickx =  318.0 bricky =  96.0 ballx =  368.9129063532961 bally =  120.68985747297117
//    brickx =  318.0 bricky =  96.0 ballx =  365.4854071797865 bally =  123.1903073156177

//    brickx =  159.0 bricky =  96.0 ballx =  152.25793687042216 bally =  116.1942149471838 tashkhis =  3
//    brickx =  159.0 bricky =  96.0 ballx =  156.1433627940404 bally =  117.89817075414456 tashkhis =  3
//    brickx =  159.0 bricky =  96.0 ballx =  160.02878871765864 bally =  119.60212656110532 tashkhis =  3
