import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class TicTacToeGUI extends JFrame implements ActionListener {
    private JButton[][] buttons;
    private JButton playAgainButton;
    private JLabel resultLabel;
    private JPanel mainPanel;
    private boolean isPlayerX;
    private static final int SIZE = 3;

    public TicTacToeGUI() {
        setTitle("Tic Tac Toe");
        setSize(300, 350);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        mainPanel = new JPanel(new GridLayout(SIZE + 2, SIZE));
        buttons = new JButton[SIZE][SIZE];

        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE; j++) {
                JButton button = new JButton("");
                button.setPreferredSize(new Dimension(100, 100));
                button.setFont(new Font("Arial", Font.BOLD, 40));
                button.addActionListener(this);
                buttons[i][j] = button;
                mainPanel.add(button);
            }
        }

        resultLabel = new JLabel("X's turn");
        resultLabel.setFont(new Font("Arial", Font.BOLD, 20));
        resultLabel.setHorizontalAlignment(SwingConstants.CENTER);
        mainPanel.add(resultLabel);

        playAgainButton = new JButton("Play Again");
        playAgainButton.addActionListener(this);
        mainPanel.add(playAgainButton);

        isPlayerX = true;

        add(mainPanel);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == playAgainButton) {
            resetGame();
            return;
        }

        JButton clickedButton = (JButton) e.getSource();
        if (!clickedButton.getText().equals("")) {
            return;
        }

        if (isPlayerX) {
            clickedButton.setText("X");
            resultLabel.setText("O's turn");
        } else {
            clickedButton.setText("O");
            resultLabel.setText("X's turn");
        }

        if (checkWin()) {
            resultLabel.setText((isPlayerX ? "X" : "O") + " wins!");
            disableButtons();
            JOptionPane.showMessageDialog(this, (isPlayerX ? "X" : "O") + " wins!", "Winner!", JOptionPane.INFORMATION_MESSAGE);
        } else if (checkDraw()) {
            resultLabel.setText("It's a draw!");
            disableButtons();
        } else {
            isPlayerX = !isPlayerX;
        }
    }

    private boolean checkWin() {
        String[][] board = new String[SIZE][SIZE];
        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE; j++) {
                board[i][j] = buttons[i][j].getText();
            }
        }

        for (int i = 0; i < SIZE; i++) {
            // Check rows
            if (board[i][0].equals(board[i][1]) && board[i][1].equals(board[i][2]) && !board[i][0].equals("")) {
                return true;
            }
            // Check columns
            if (board[0][i].equals(board[1][i]) && board[1][i].equals(board[2][i]) && !board[0][i].equals("")) {
                return true;
            }
        }

        // Check diagonals
        if (board[0][0].equals(board[1][1]) && board[1][1].equals(board[2][2]) && !board[0][0].equals("")) {
            return true;
        }
        if (board[0][2].equals(board[1][1]) && board[1][1].equals(board[2][0]) && !board[0][2].equals("")) {
            return true;
        }

        return false;
    }

    private boolean checkDraw() {
        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE; j++) {
                if (buttons[i][j].getText().equals("")) {
                    return false;
                }
            }
        }
        return true;
    }

    private void disableButtons() {
        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE; j++) {
                buttons[i][j].setEnabled(false);
            }
        }
    }

    private void resetGame() {
        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE; j++) {
                buttons[i][j].setText("");
                buttons[i][j].setEnabled(true);
            }
        }
        resultLabel.setText("X's turn");
        isPlayerX = true;
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            TicTacToeGUI game = new TicTacToeGUI();
            game.setVisible(true);
        });
    }
}
