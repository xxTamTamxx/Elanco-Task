# Elanco-Task

import java.io.File;

import java.io.FileNotFoundException;

import java.util.Scanner;

import java.awt.EventQueue;

import javax.swing.JFrame;

import javax.swing.JPanel;

import javax.swing.border.EmptyBorder;

import javax.swing.JLabel;

import java.awt.Font;

import java.awt.Color;

import javax.swing.JButton;

import javax.swing.JScrollPane;

import javax.swing.JTable;

import javax.swing.table.DefaultTableModel;

import java.awt.event.ActionListener;

import java.awt.event.ActionEvent;

public class ElancoMain extends JFrame {

	private JPanel contentPane;
	private JTable table;
	private JTable table_1;

	/**
	 * Launch the application.
	 */
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					ElancoMain frame = new ElancoMain();
					frame.setVisible(true);
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the frame.
	 */
	public ElancoMain() {
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setBounds(100, 100, 1465, 800);
		contentPane = new JPanel();
		contentPane.setBackground(new Color(255, 255, 255));
		contentPane.setForeground(Color.WHITE);
		contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));
		setContentPane(contentPane);
		contentPane.setLayout(null);
		
		JLabel lblNewLabel = new JLabel("Elanco Data");
		lblNewLabel.setBackground(new Color(0, 0, 0));
		lblNewLabel.setForeground(new Color(105, 105, 105));
		lblNewLabel.setFont(new Font("Tw Cen MT Condensed", Font.BOLD, 40));
		lblNewLabel.setBounds(626, 11, 174, 48);
		contentPane.add(lblNewLabel);
		
		JPanel panel = new JPanel();
		panel.setBackground(new Color(51, 102, 153));
		panel.setIgnoreRepaint(true);
		panel.setForeground(new Color(51, 102, 153));
		panel.setBounds(10, 49, 1429, 701);
		contentPane.add(panel);
		panel.setLayout(null);
		
		JButton btnNewButton = new JButton("Raw Data");
		btnNewButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				try
				{
					File my0bj = new File("D:\\MAIN FOLDER\\ElancoTask/Elanco Data.csv");
					Scanner myReader = new Scanner(my0bj);
					
					while (myReader.hasNextLine())
					{
						String[] data = myReader.nextLine().split(",");
						String CQ = data[0];
						String C = data[1];
						String D = data[2];
						String ID = data[3];
						String MC = data[4];
						String RG = data[5];
						String RL = data[6];
						String AN = data[7];
						String E = data[8];
						String BU = data[9];
						String UOM = data[10];
						String SM = data[11];
						String EE = data[12];
						
						DefaultTableModel model = (DefaultTableModel)table.getModel();
						model.addRow(new String[] {CQ, C, D, ID, MC, RG, RL, AN, E, BU, UOM, SM, EE});
					}
					myReader.close();
				}
				catch (FileNotFoundException e1)
				{
					System.out.println("File cannot be found.");
					e1.printStackTrace();
				}
			}
			
		});
		btnNewButton.setBackground(new Color(255, 255, 255));
		btnNewButton.setForeground(new Color(51, 102, 153));
		btnNewButton.setFont(new Font("Tw Cen MT Condensed", Font.PLAIN, 20));
		btnNewButton.setBounds(20, 11, 129, 31);
		panel.add(btnNewButton);
		
		JScrollPane scrollPane = new JScrollPane();
		scrollPane.setBounds(20, 53, 1399, 250);
		panel.add(scrollPane);
		
		table = new JTable();
		table.setModel(new DefaultTableModel(
			new Object[][] {
			},
			new String[] {
				"Consumed Quantity", "Cost", "Date", "Instance ID", "Meter Category", "Resource Group", "Resource Location", "App Name", "Environment", "Business Unit", "Unit Of Measure", "Location", "Service Name"
			}
		) {
			Class[] columnTypes = new Class[] {
				String.class, String.class, String.class, String.class, String.class, String.class, String.class, String.class, String.class, String.class, String.class, String.class, String.class
			};
			public Class getColumnClass(int columnIndex) {
				return columnTypes[columnIndex];
			}
			boolean[] columnEditables = new boolean[] {
				false, false, false, false, false, false, false, false, false, false, false, false, false
			};
			public boolean isCellEditable(int row, int column) {
				return columnEditables[column];
			}
		});
		table.getColumnModel().getColumn(0).setPreferredWidth(107);
		table.getColumnModel().getColumn(4).setPreferredWidth(87);
		table.getColumnModel().getColumn(5).setPreferredWidth(87);
		table.getColumnModel().getColumn(6).setPreferredWidth(98);
		table.getColumnModel().getColumn(10).setPreferredWidth(89);
		scrollPane.setViewportView(table);
		
		JScrollPane scrollPane_1 = new JScrollPane();
		scrollPane_1.setBounds(20, 394, 1399, 281);
		panel.add(scrollPane_1);
		
		table_1 = new JTable();
		table_1.setModel(new DefaultTableModel(
			new Object[][] {
			},
			new String[] {
				"Consumed Quantity", "Cost", "Date", "Instance ID", "Meter Category", "Resource Group", "Resource Location", "App Name", "Environment", "Business Unit", "Unit Of Measure", "Location", "Service Name"
			}
		) {
			Class[] columnTypes = new Class[] {
				String.class, String.class, String.class, String.class, String.class, String.class, String.class, String.class, String.class, String.class, String.class, String.class, String.class
			};
			public Class getColumnClass(int columnIndex) {
				return columnTypes[columnIndex];
			}
			boolean[] columnEditables = new boolean[] {
				false, false, false, false, false, false, false, false, false, false, false, false, false
			};
			public boolean isCellEditable(int row, int column) {
				return columnEditables[column];
			}
		});
		table_1.getColumnModel().getColumn(10).setPreferredWidth(88);
		scrollPane_1.setViewportView(table_1);
		
		JButton btnHighToLow = new JButton("Cost High to Low");
		btnHighToLow.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				try
				{
					File my0bj = new File("D:\\MAIN FOLDER\\ElancoTask/Elanco Sorted By Cost Highest.csv");
					Scanner myReader = new Scanner(my0bj);
					
					while (myReader.hasNextLine())
					{
						String[] data = myReader.nextLine().split(",");
						String CQ = data[0];
						String C = data[1];
						String D = data[2];
						String ID = data[3];
						String MC = data[4];
						String RG = data[5];
						String RL = data[6];
						String AN = data[7];
						String E = data[8];
						String BU = data[9];
						String UOM = data[10];
						String SM = data[11];
						String EE = data[12];
						
						DefaultTableModel model = (DefaultTableModel)table_1.getModel();
						model.addRow(new String[] {CQ, C, D, ID, MC, RG, RL, AN, E, BU, UOM, SM, EE});
					}
					myReader.close();
				}
				catch (FileNotFoundException e1)
				{
					System.out.println("File cannot be found.");
					e1.printStackTrace();
				}
			}
			
		});
		btnHighToLow.setForeground(new Color(51, 102, 153));
		btnHighToLow.setFont(new Font("Tw Cen MT Condensed", Font.PLAIN, 20));
		btnHighToLow.setBackground(Color.WHITE);
		btnHighToLow.setBounds(20, 352, 146, 31);
		panel.add(btnHighToLow);
		
		JButton btnHighToLow_1 = new JButton("Cost Low to High");
		btnHighToLow_1.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				try
				{
					File my0bj = new File("D:\\MAIN FOLDER\\ElancoTask/ElancoCLTOH.csv");
					Scanner myReader = new Scanner(my0bj);
					
					while (myReader.hasNextLine())
					{
						String[] data = myReader.nextLine().split(",");
						String CQ = data[0];
						String C = data[1];
						String D = data[2];
						String ID = data[3];
						String MC = data[4];
						String RG = data[5];
						String RL = data[6];
						String AN = data[7];
						String E = data[8];
						String BU = data[9];
						String UOM = data[10];
						String SM = data[11];
						String EE = data[12];
						
						DefaultTableModel model = (DefaultTableModel)table_1.getModel();
						model.addRow(new String[] {CQ, C, D, ID, MC, RG, RL, AN, E, BU, UOM, SM, EE});
					}
					myReader.close();
				}
				catch (FileNotFoundException e1)
				{
					System.out.println("File cannot be found.");
					e1.printStackTrace();
				}
			}
			
		});
		btnHighToLow_1.setForeground(new Color(51, 102, 153));
		btnHighToLow_1.setFont(new Font("Tw Cen MT Condensed", Font.PLAIN, 20));
		btnHighToLow_1.setBackground(Color.WHITE);
		btnHighToLow_1.setBounds(184, 352, 146, 31);
		panel.add(btnHighToLow_1);
		
		JButton btnHighToLow_1_1 = new JButton("Delete Table Values");
		btnHighToLow_1_1.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				DefaultTableModel dtm = (DefaultTableModel) table_1.getModel();
				dtm.setRowCount(0);
			}
		});
		btnHighToLow_1_1.setForeground(new Color(255, 255, 255));
		btnHighToLow_1_1.setFont(new Font("Tw Cen MT Condensed", Font.PLAIN, 20));
		btnHighToLow_1_1.setBackground(new Color(102, 0, 0));
		btnHighToLow_1_1.setBounds(1249, 352, 170, 31);
		panel.add(btnHighToLow_1_1);
		
		JButton btnHighToLow_1_1_1 = new JButton("Delete Table Values");
		btnHighToLow_1_1_1.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
					DefaultTableModel dtm = (DefaultTableModel) table.getModel();
					dtm.setRowCount(0);
				}
			});
		btnHighToLow_1_1_1.setForeground(Color.WHITE);
		btnHighToLow_1_1_1.setFont(new Font("Tw Cen MT Condensed", Font.PLAIN, 20));
		btnHighToLow_1_1_1.setBackground(new Color(102, 0, 0));
		btnHighToLow_1_1_1.setBounds(1249, 17, 170, 31);
		panel.add(btnHighToLow_1_1_1);
		
		JButton btnHighToLow_1_2 = new JButton("CQ Low to High");
		btnHighToLow_1_2.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				try
				{
					File my0bj = new File("D:\\MAIN FOLDER\\ElancoTask/CQLTH.csv");
					Scanner myReader = new Scanner(my0bj);
					
					while (myReader.hasNextLine())
					{
						String[] data = myReader.nextLine().split(",");
						String CQ = data[0];
						String C = data[1];
						String D = data[2];
						String ID = data[3];
						String MC = data[4];
						String RG = data[5];
						String RL = data[6];
						String AN = data[7];
						String E = data[8];
						String BU = data[9];
						String UOM = data[10];
						String SM = data[11];
						String EE = data[12];
						
						DefaultTableModel model = (DefaultTableModel)table_1.getModel();
						model.addRow(new String[] {CQ, C, D, ID, MC, RG, RL, AN, E, BU, UOM, SM, EE});
					}
					myReader.close();
				}
				catch (FileNotFoundException e1)
				{
					System.out.println("File cannot be found.");
					e1.printStackTrace();
				}
			}
			
		});
		btnHighToLow_1_2.setForeground(new Color(51, 102, 153));
		btnHighToLow_1_2.setFont(new Font("Tw Cen MT Condensed", Font.PLAIN, 20));
		btnHighToLow_1_2.setBackground(Color.WHITE);
		btnHighToLow_1_2.setBounds(517, 352, 146, 31);
		panel.add(btnHighToLow_1_2);
		
		JButton btnHighToLow_1_2_1 = new JButton("CQ High to Low");
		btnHighToLow_1_2_1.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {try
			{
				File my0bj = new File("D:\\MAIN FOLDER\\ElancoTask/CQHTL.csv");
				Scanner myReader = new Scanner(my0bj);
				
				while (myReader.hasNextLine())
				{
					String[] data = myReader.nextLine().split(",");
					String CQ = data[0];
					String C = data[1];
					String D = data[2];
					String ID = data[3];
					String MC = data[4];
					String RG = data[5];
					String RL = data[6];
					String AN = data[7];
					String E = data[8];
					String BU = data[9];
					String UOM = data[10];
					String SM = data[11];
					String EE = data[12];
					
					DefaultTableModel model = (DefaultTableModel)table_1.getModel();
					model.addRow(new String[] {CQ, C, D, ID, MC, RG, RL, AN, E, BU, UOM, SM, EE});
				}
				myReader.close();
			}
			catch (FileNotFoundException e1)
			{
				System.out.println("File cannot be found.");
				e1.printStackTrace();
			}
		}
		
	});
		btnHighToLow_1_2_1.setForeground(new Color(51, 102, 153));
		btnHighToLow_1_2_1.setFont(new Font("Tw Cen MT Condensed", Font.PLAIN, 20));
		btnHighToLow_1_2_1.setBackground(Color.WHITE);
		btnHighToLow_1_2_1.setBounds(350, 352, 146, 31);
		panel.add(btnHighToLow_1_2_1);
	}
}
