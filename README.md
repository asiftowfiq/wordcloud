import javax.swing.*;
import java.awt.*;
import java.util.Random;

public class NameShapeWordCloud extends JPanel {

    private static final int WIDTH = 1500;
    private static final int HEIGHT = 900;

    private static final String[] names = {
            "asif", "asib", "mridul", "abir", "nafiz", "minhaj", "darda", "ayshi", "mim",
            "ayon", "sayam", "rocky", "aronno", "maruf", "ifti", "mushfik", "rifat",
            "tasmia", "onik", "medha", "tinni", "soumik", "shuvo", "mahir", "ananya",
            "opu", "saad", "arif", "nishat", "sani", "disha", "saied", "moslah", "robi",
            "alam", "naib", "rashid"
    };


    private static final int GRID_SIZE = 25;
    private static final int FONT_SIZE = 12;
    private static final int SPACING = 35;

    private static final int START_X = 50;
    private static final int START_Y = 100;


    public NameShapeWordCloud() {
        this.setPreferredSize(new Dimension(WIDTH, HEIGHT));
    }

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        Graphics2D g2d = (Graphics2D) g;


        g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);

        Font font = new Font("Arial", Font.PLAIN, FONT_SIZE);
        g2d.setFont(font);


        drawLetter(g2d, "C", START_X, START_Y);
        drawLetter(g2d, "S", START_X + SPACING * 6, START_Y);
        drawLetter(g2d, "E", START_X + SPACING * 12, START_Y);
        drawLetter(g2d, "6", START_X + SPACING * 18, START_Y);
        drawLetter(g2d, "4", START_X + SPACING * 24, START_Y);
        drawLetter(g2d, "K", START_X + SPACING * 30, START_Y);
    }

    private void drawLetter(Graphics2D g2d, String letter, int startX, int startY) {
        String[][] letterGrid = getLetterGrid(letter);

        for (int row = 0; row < letterGrid.length; row++) {
            for (int col = 0; col < letterGrid[row].length; col++) {
                if (!letterGrid[row][col].equals(" ")) {// Select a random name from the list
                    String name = names[new Random().nextInt(names.length)];

                    g2d.setColor(new Color(new Random().nextInt(255), new Random().nextInt(255), new Random().nextInt(255)));


                    g2d.drawString(name, startX + col * GRID_SIZE, startY + row * SPACING);
                }
            }
        }
    }

    private String[][] getLetterGrid(String letter) {
        switch (letter) {
            case "C":
                return new String[][]{
                        {" ", "C", "C", "C", "C", " "},
                        {"C", " ", " ", " ", " ", "C"},
                        {"C", " ", " ", " ", " ", " "},
                        {"C", " ", " ", " ", " ", " "},
                        {"C", " ", " ", " ", " ", " "},
                        {"C", " ", " ", " ", " ", "C"},
                        {" ", "C", "C", "C", "C", " "}
                };
            case "S":
                return new String[][]{
                        {"S", "S", "S", "S", "S"},
                        {"S", " ", " ", " ", " "},
                        {"S", " ", " ", " ", " "},
                        {"S", "S", "S", "S", "S"},
                        {" ", " ", " ", " ", "S"},
                        {" ", " ", " ", " ", "S"},
                        {"S", "S", "S", "S", "S"}
                };
            case "E":
                return new String[][]{
                        {"E", "E", "E", "E", "E"},
                        {"E", " ", " ", " ", " "},
                        {"E", " ", " ", " ", " "},
                        {"E", "E", "E", "E", " "},
                        {"E", " ", " ", " ", " "},
                        {"E", " ", " ", " ", " "},
                        {"E", "E", "E", "E", "E"}
                };
            case "6":
                return new String[][]{
                        {" ", "6", "6", "6", " "},
                        {"6", " ", " ", " ", " "},
                        {"6", " ", " ", " ", " "},
                        {"6", " ", " ", " ", " "},
                        {"6", " ", "6", "6", " "},
                        {"6", " ", "6", "6", " "},
                        {" ", "6", "6", "6", " "}
                };
            case "4":
                return new String[][]{
                        {" ", " ", " ", "4", " "},
                        {" ", " ", " ", "4", " "},
                        {" ", " ", "4", "4", " "},
                        {" ", "4", " ", "4", " "},
                        {"4", "4", "4", "4", "4"},
                        {" ", " ", " ", "4", " "},
                        {" ", " ", " ", "4", " "}
                };
            case "K":
                return new String[][]{
                        {"K", " ", " ", " ", "K"},
                        {"K", " ", " ", "K", " "},
                        {"K", " ", "K", " ", " "},
                        {"K", "K", " ", " ", " "},
                        {"K", " ", "K", " ", " "},
                        {"K", " ", " ", "K", " "},
                        {"K", " ", " ", " ", "K"}

                };
            default:
                return new String[][]{{}};
        }
    }

    public static void main(String[] args) {

        JFrame frame = new JFrame("Name Shape Word Cloud");
        NameShapeWordCloud wordCloud = new NameShapeWordCloud();
        frame.add(wordCloud);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.pack();
        frame.setLocationRelativeTo(null);
        frame.setVisible(true);
    }
}
