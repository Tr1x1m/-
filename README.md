Form1
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Data.SqlClient;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace web_spravochnik
{
    public partial class Form1 : Form
    {

        SqlConnection sql = new SqlConnection(@"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=C:\Users\steam\source\repos\web_spravochnik\web_spravochnik\Database1.mdf;Integrated Security=True");

        public static bool flag = false;

        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {

            int schetchik;
            schetchik = 0;

            if(flag == true)
            {
                flag = false;
                schetchik++;
                
            }
            HTML5 newForm = new HTML5();
            newForm.Show();

        }

        private void button2_Click(object sender, EventArgs e)
        {
            int schetchik1;
            schetchik1 = 0;

            if (flag == true)
            {
                flag = false;
                schetchik1++;
            }
            CSS newForm = new CSS();
            newForm.Show();
        }

        private void button3_Click(object sender, EventArgs e)
        {
            int schetchik2;
            schetchik2 = 0;

            if (flag == true)
            {
                flag = false;
                schetchik2++;
            }
            JS newForm = new JS();
            newForm.Show();
        }

        private void button4_Click(object sender, EventArgs e)
        {
            int schetchik3;
            schetchik3 = 0;

            if (flag == true)
            {
                flag = false;
                schetchik3++;
            }
            PHP newForm = new PHP();
            newForm.Show();
        }

        private void button5_Click(object sender, EventArgs e)
        {
            int schetchik4;
            schetchik4 = 0;

            if (flag == true)
            {
                flag = false;
                schetchik4++;
            }
            BD newForm = new BD();
            newForm.Show();
        }

        private void dataGridView1_CellContentClick(object sender, DataGridViewCellEventArgs e)
        {

        }

        private void button6_Click(object sender, EventArgs e)
        {
            void FillDataGridView()
            {
                if (sql.State == ConnectionState.Closed)
                    sql.Open();
                SqlDataAdapter sqlData = new SqlDataAdapter("Search", sql);
                sqlData.SelectCommand.CommandType = CommandType.StoredProcedure;
                sqlData.SelectCommand.Parameters.AddWithValue("Id", textBox1.Text);
                DataTable dataTable = new DataTable();
                sqlData.Fill(dataTable);
                dataGridView1.DataSource = dataTable;
                dataGridView1.Columns[0].Visible = false;
                sql.Close();

            }
            try
            {
                FillDataGridView();
            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message, "Error Message");
            }

           
        }
    }
}

CSS Form


using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace web_spravochnik
{
    public partial class CSS : Form
    {
        public CSS()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            CSS newForm1 = new CSS();
            newForm1.Close();
            Form1 newForm = new Form1();
            newForm.Show();
        }

        private void CSS_Load(object sender, EventArgs e)
        {

        }
    }
}

BD Form


using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace web_spravochnik
{
    public partial class BD : Form
    {
        public BD()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            Form1 newForm = new Form1();
            BD newForm1 = new BD();
            newForm.Show();
            newForm1.Hide();
        }

        private void BD_Load(object sender, EventArgs e)
        {

        }
    }
}


HTML5 Form


using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace web_spravochnik
{
    public partial class HTML5 : Form
    {
        public HTML5()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            HTML5 newForm1 = new HTML5();
            newForm1.Close();
            Form1 newForm = new Form1();
            newForm.Show();
        }

        private void HTML5_Load(object sender, EventArgs e)
        {

        }
    }
}

JS Form

using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace web_spravochnik
{
    public partial class JS : Form
    {
        public JS()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            JS newForm1 = new JS();
            newForm1.Close();
            Form1 newForm = new Form1();
            newForm.Show();
        }

        private void JS_Load(object sender, EventArgs e)
        {

        }
    }
}

PHP Form

using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace web_spravochnik
{
    public partial class PHP : Form
    {
        public PHP()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            PHP newForm1 = new PHP();
            newForm1.Close();
            Form1 newForm = new Form1();
            newForm.Show();
            
        }

        private void PHP_Load(object sender, EventArgs e)
        {

        }
    }
}



CREATE TABLE [dbo].[Table1] (
    [Id]         INT IDENTITY (1, 1) NOT NULL,
    [schetchik]  INT NULL,
    [schetchik1] INT NULL,
    [schetchik2] INT NULL,
    [schetchik3] INT NULL,
    [schetchik4] INT NULL,
    PRIMARY KEY CLUSTERED ([Id] ASC)
);


CREATE PROCEDURE [dbo].[Procedure]
	@mode NVARCHAR(MAX),
	@Id int,
	@schetchik int,
	@schetchik1 int,
	@schetchik2 int,
	@schetchik3 int,
	@schetchik4 int
AS
	if @mode = 'Add'
	BEGIN
	INSERT INTO Table1
	(
	schetchik,
	schetchik1,
	schetchik2,
	schetchik3,
	schetchik4
	)
	VALUES
	(
	@schetchik,
	@schetchik1,
	@schetchik2,
	@schetchik3,
	@schetchik4
	)
	END



CREATE PROCEDURE [dbo].[search]
	@Id int
AS
	SELECT *
	FROM Table1
	WHERE
	( 
	
	Id like @Id+''
	
 )
