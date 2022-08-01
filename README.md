# Watch_Shop


cơ sơ dữ liệu 



/*------------------------------------------- */

CREATE DATABASE Shop_DongHo

USE [Shop_DongHo]

/*------------------------------------------- */



GO
/****** Object:  Table [dbo].[Category]    Script Date: 2022-05-07 10:34:56 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Category](
	[Category_ID] [int] IDENTITY(1,1) NOT NULL,
	[Category_Name] [nvarchar](50) NULL,
 CONSTRAINT [PK_Category] PRIMARY KEY CLUSTERED 
(
	[Category_ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Contact]    Script Date: 2022-05-07 10:34:56 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Contact](
	[Contact_ID] [int] IDENTITY(1,1) NOT NULL,
	[Name] [nvarchar](50) NULL,
	[Email] [nvarchar](50) NULL,
	[Title] [nvarchar](max) NULL,
	[Message] [nvarchar](max) NULL,
	[Create_Date] [datetime] NULL,
	[Status] [int] NULL,
 CONSTRAINT [PK_Contact] PRIMARY KEY CLUSTERED 
(
	[Contact_ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Customer_Product]    Script Date: 2022-05-07 10:34:56 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Customer_Product](
	[Customer_ID] [int] NOT NULL,
	[Product_ID] [int] NOT NULL,
	[CusPro_Name] [nvarchar](50) NULL,
	[CusPro_Price] [decimal](18, 0) NULL,
	[CusPro_Image] [nvarchar](50) NULL,
 CONSTRAINT [PK_Customer_Product] PRIMARY KEY CLUSTERED 
(
	[Customer_ID] ASC,
	[Product_ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Discount]    Script Date: 2022-05-07 10:34:56 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Discount](
	[Discount_ID] [int] IDENTITY(1,1) NOT NULL,
	[Discount_Name] [nchar](50) NULL,
	[Discount_Price] [decimal](18, 0) NULL,
	[Discount_Quantity] [int] NULL,
	[Expiration_Date] [date] NULL,
 CONSTRAINT [PK_Discount] PRIMARY KEY CLUSTERED 
(
	[Discount_ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[FeedBack]    Script Date: 2022-05-07 10:34:56 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[FeedBack](
	[FeedBack_ID] [int] IDENTITY(1,1) NOT NULL,
	[FeedBack_User] [nvarchar](50) NULL,
	[FeedBack_Content] [nvarchar](max) NULL,
	[FeedBack_Time] [datetime] NULL,
	[Product_ID] [int] NULL,
 CONSTRAINT [PK_FeedBack] PRIMARY KEY CLUSTERED 
(
	[FeedBack_ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Import]    Script Date: 2022-05-07 10:34:56 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Import](
	[Import_ID] [int] IDENTITY(1,1) NOT NULL,
	[Importer] [nvarchar](50) NULL,
	[Import_Date] [date] NULL,
	[Import_Total] [decimal](18, 0) NULL,
	[Import_Note] [nvarchar](max) NULL,
	[Provider_ID] [int] NULL,
 CONSTRAINT [PK_Import] PRIMARY KEY CLUSTERED 
(
	[Import_ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Import_Details]    Script Date: 2022-05-07 10:34:56 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Import_Details](
	[Import_Details_ID] [int] IDENTITY(1,1) NOT NULL,
	[Import_ID] [int] NOT NULL,
	[Product_ID] [int] NOT NULL,
	[Quantity] [int] NULL,
	[Price] [decimal](18, 0) NULL,
	[Into_Money] [decimal](18, 0) NULL,
 CONSTRAINT [PK_Import_Details_1] PRIMARY KEY CLUSTERED 
(
	[Import_Details_ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[OrderDetail]    Script Date: 2022-05-07 10:34:56 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[OrderDetail](
	[OrderID_STT] [int] IDENTITY(1,1) NOT NULL,
	[Order_ID] [int] NOT NULL,
	[Product_ID] [int] NOT NULL,
	[Product_Name] [nvarchar](100) NULL,
	[Product_Quantity] [int] NULL,
	[Into_Money] [decimal](18, 0) NULL,
	[Status] [bit] NULL,
 CONSTRAINT [PK_OrderDetail_1] PRIMARY KEY CLUSTERED 
(
	[OrderID_STT] ASC,
	[Order_ID] ASC,
	[Product_ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Orders]    Script Date: 2022-05-07 10:34:56 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Orders](
	[Order_ID] [int] IDENTITY(1,1) NOT NULL,
	[UserID] [int] NULL,
	[Name] [nvarchar](100) NULL,
	[Email] [nvarchar](50) NULL,
	[Phone] [nchar](12) NULL,
	[Address] [nvarchar](100) NULL,
	[Create_Date] [date] NULL,
	[City] [nvarchar](50) NULL,
	[Note] [nvarchar](100) NULL,
	[Total] [decimal](18, 0) NULL,
	[Discount] [decimal](18, 0) NULL,
	[Status] [nvarchar](max) NULL,
	[Point] [int] NULL,
 CONSTRAINT [PK_Orders] PRIMARY KEY CLUSTERED 
(
	[Order_ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Product]    Script Date: 2022-05-07 10:34:56 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Product](
	[Product_ID] [int] IDENTITY(1,1) NOT NULL,
	[Product_Name] [nvarchar](100) NULL,
	[Price] [decimal](18, 0) NULL,
	[Quantity] [int] NULL,
	[Description] [nvarchar](500) NULL,
	[Image] [nvarchar](50) NULL,
	[Aparatus and Energy] [nvarchar](50) NULL,
	[Material_Day] [nvarchar](50) NULL,
	[Material_Matkinh] [nvarchar](50) NULL,
	[Dial_HinhDang] [nvarchar](50) NULL,
	[Dial_KichThuoc] [nvarchar](50) NULL,
	[Dial_MauSac] [nvarchar](50) NULL,
	[Waterproof] [nvarchar](50) NULL,
	[TradeMark] [nvarchar](50) NULL,
	[Origin] [nvarchar](50) NULL,
	[Category_ID] [int] NULL,
	[Sales] [int] NULL,
	[ImageLink] [varchar](max) NULL,
 CONSTRAINT [PK_Product] PRIMARY KEY CLUSTERED 
(
	[Product_ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Providerr]    Script Date: 2022-05-07 10:34:56 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Providerr](
	[Provider_ID] [int] IDENTITY(1,1) NOT NULL,
	[Provider_Name] [nvarchar](50) NULL,
 CONSTRAINT [PK_Providerr] PRIMARY KEY CLUSTERED 
(
	[Provider_ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Users]    Script Date: 2022-05-07 10:34:56 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Users](
	[UserID] [int] IDENTITY(1,1) NOT NULL,
	[Username] [nvarchar](50) NULL,
	[Password] [nvarchar](50) NULL,
	[Permission] [int] NULL,
	[CustomerName] [nvarchar](50) NULL,
	[CustomerEmail] [nvarchar](50) NULL,
	[CustomerPhone] [nchar](12) NULL,
	[CustomerAddress] [nvarchar](100) NULL,
	[CustomerCity] [nvarchar](50) NULL,
	[CustomerToken] [nvarchar](50) NULL,
	[RewardPoints] [int] NULL,
 CONSTRAINT [PK_Users] PRIMARY KEY CLUSTERED 
(
	[UserID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
SET IDENTITY_INSERT [dbo].[Category] ON 

INSERT [dbo].[Category] ([Category_ID], [Category_Name]) VALUES (1, N'Đồng hồ nam')
INSERT [dbo].[Category] ([Category_ID], [Category_Name]) VALUES (2, N'Đồng hồ nữ')
INSERT [dbo].[Category] ([Category_ID], [Category_Name]) VALUES (3, N'Đồng hồ đôi')
INSERT [dbo].[Category] ([Category_ID], [Category_Name]) VALUES (4, N'Dây da Hirshch')
INSERT [dbo].[Category] ([Category_ID], [Category_Name]) VALUES (5, N'Dây da SRC')
SET IDENTITY_INSERT [dbo].[Category] OFF
GO
SET IDENTITY_INSERT [dbo].[Contact] ON 

INSERT [dbo].[Contact] ([Contact_ID], [Name], [Email], [Title], [Message], [Create_Date], [Status]) VALUES (24, N'Nguyễn Văn Sơn', N'sonnguyeng2001@gmail.com', N'where', N'where
', CAST(N'2022-04-04T17:26:53.027' AS DateTime), 0)
INSERT [dbo].[Contact] ([Contact_ID], [Name], [Email], [Title], [Message], [Create_Date], [Status]) VALUES (25, N'Nguyễn Văn Sơn', N'sonnguyeng2001@gmail.com', N'where', N'where
', CAST(N'2022-04-04T17:30:40.270' AS DateTime), 0)
SET IDENTITY_INSERT [dbo].[Contact] OFF
GO
INSERT [dbo].[Customer_Product] ([Customer_ID], [Product_ID], [CusPro_Name], [CusPro_Price], [CusPro_Image]) VALUES (7, 2, NULL, NULL, NULL)
INSERT [dbo].[Customer_Product] ([Customer_ID], [Product_ID], [CusPro_Name], [CusPro_Price], [CusPro_Image]) VALUES (7, 7, NULL, NULL, NULL)
INSERT [dbo].[Customer_Product] ([Customer_ID], [Product_ID], [CusPro_Name], [CusPro_Price], [CusPro_Image]) VALUES (7, 8, NULL, NULL, NULL)
GO
SET IDENTITY_INSERT [dbo].[Discount] ON 

INSERT [dbo].[Discount] ([Discount_ID], [Discount_Name], [Discount_Price], [Discount_Quantity], [Expiration_Date]) VALUES (29, N'NEWDISCOUNT                                       ', CAST(100000 AS Decimal(18, 0)), 0, CAST(N'2022-04-30' AS Date))
INSERT [dbo].[Discount] ([Discount_ID], [Discount_Name], [Discount_Price], [Discount_Quantity], [Expiration_Date]) VALUES (31, N'NAME                                              ', CAST(200000 AS Decimal(18, 0)), 8, CAST(N'2022-04-30' AS Date))
INSERT [dbo].[Discount] ([Discount_ID], [Discount_Name], [Discount_Price], [Discount_Quantity], [Expiration_Date]) VALUES (32, N'DISCOUNT                                          ', CAST(1000000 AS Decimal(18, 0)), 11, CAST(N'2022-05-14' AS Date))
SET IDENTITY_INSERT [dbo].[Discount] OFF
GO
SET IDENTITY_INSERT [dbo].[FeedBack] ON 

INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (12, N'sonnguyeng2001@gmail.com', N'1', CAST(N'2021-12-30T16:33:04.050' AS DateTime), 5)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (14, N'sonnguyeng2001@gmail.com', N'1', CAST(N'2021-12-30T17:08:10.913' AS DateTime), 18)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (26, N'sonnguyeng2001@gmail.com', N'không', CAST(N'2022-01-05T22:17:27.420' AS DateTime), 9)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (27, N'nguyenvandung251210@gmail.com', N'No', CAST(N'2022-01-21T20:20:45.553' AS DateTime), 5)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (52, N'sonnguyeng2001@gmail.com', N'dasdasdasdas', CAST(N'2022-03-19T16:08:29.370' AS DateTime), 2)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (54, N'sonnguyeng2001@gmail.com', N'Khoong', CAST(N'2022-03-29T21:27:33.057' AS DateTime), 2)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (1054, N'nguyenvandung251210@gmail.com', N'No Comment !!!', CAST(N'2022-04-14T21:12:39.060' AS DateTime), 2)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (1055, N'nguyenvandung251210@gmail.com', N'Test comment', CAST(N'2022-04-14T21:19:34.430' AS DateTime), 2)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (1057, N'nguyenvandung251210@gmail.com', N'No comment', CAST(N'2022-04-14T21:27:54.783' AS DateTime), 3)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (1058, N'nguyenvandung251210@gmail.com', N'New Comment', CAST(N'2022-04-14T21:29:28.387' AS DateTime), 3)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (1059, N'nguyenvandung251210@gmail.com', N'Test', CAST(N'2022-04-14T21:34:18.230' AS DateTime), 3)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (1112, N'nguyenvandung251210@gmail.com', N'no', CAST(N'2022-04-23T10:29:50.417' AS DateTime), 8)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (1113, N'nguyenvandung251210@gmail.com', N'no', CAST(N'2022-04-23T10:29:51.837' AS DateTime), 8)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (1114, N'nguyenvandung251210@gmail.com', N'no', CAST(N'2022-04-23T10:29:52.783' AS DateTime), 8)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (1115, N'nguyenvandung251210@gmail.com', N'no', CAST(N'2022-04-23T10:29:54.567' AS DateTime), 8)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (1116, N'nguyenvandung251210@gmail.com', N'No comment', CAST(N'2022-05-07T09:45:56.157' AS DateTime), 7)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (1117, N'nguyenvandung251210@gmail.com', N'No comment', CAST(N'2022-05-07T09:46:01.133' AS DateTime), 7)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (1118, N'nguyenvandung251210@gmail.com', N'No comment', CAST(N'2022-05-07T09:46:02.337' AS DateTime), 7)
INSERT [dbo].[FeedBack] ([FeedBack_ID], [FeedBack_User], [FeedBack_Content], [FeedBack_Time], [Product_ID]) VALUES (1119, N'nguyenvandung251210@gmail.com', N'No comment', CAST(N'2022-05-07T09:46:03.690' AS DateTime), 7)
SET IDENTITY_INSERT [dbo].[FeedBack] OFF
GO
SET IDENTITY_INSERT [dbo].[Import] ON 

INSERT [dbo].[Import] ([Import_ID], [Importer], [Import_Date], [Import_Total], [Import_Note], [Provider_ID]) VALUES (9, N'No Importer ', CAST(N'2022-03-26' AS Date), CAST(7368000 AS Decimal(18, 0)), N'No Note', 1)
INSERT [dbo].[Import] ([Import_ID], [Importer], [Import_Date], [Import_Total], [Import_Note], [Provider_ID]) VALUES (1013, N'No Importer', CAST(N'2022-04-10' AS Date), CAST(16920000 AS Decimal(18, 0)), N'Note', 1)
INSERT [dbo].[Import] ([Import_ID], [Importer], [Import_Date], [Import_Total], [Import_Note], [Provider_ID]) VALUES (1014, N'Casio Sekko Tissots', CAST(N'2022-04-11' AS Date), CAST(128120000 AS Decimal(18, 0)), N'No', 1)
SET IDENTITY_INSERT [dbo].[Import] OFF
GO
SET IDENTITY_INSERT [dbo].[Import_Details] ON 

INSERT [dbo].[Import_Details] ([Import_Details_ID], [Import_ID], [Product_ID], [Quantity], [Price], [Into_Money]) VALUES (18, 9, 7, 2, CAST(3684000 AS Decimal(18, 0)), CAST(7368000 AS Decimal(18, 0)))
INSERT [dbo].[Import_Details] ([Import_Details_ID], [Import_ID], [Product_ID], [Quantity], [Price], [Into_Money]) VALUES (1024, 1013, 21, 4, CAST(4230000 AS Decimal(18, 0)), CAST(16920000 AS Decimal(18, 0)))
INSERT [dbo].[Import_Details] ([Import_Details_ID], [Import_ID], [Product_ID], [Quantity], [Price], [Into_Money]) VALUES (1026, 1014, 7, 5, CAST(3684000 AS Decimal(18, 0)), CAST(18420000 AS Decimal(18, 0)))
INSERT [dbo].[Import_Details] ([Import_Details_ID], [Import_ID], [Product_ID], [Quantity], [Price], [Into_Money]) VALUES (1027, 1014, 8, 5, CAST(21940000 AS Decimal(18, 0)), CAST(109700000 AS Decimal(18, 0)))
SET IDENTITY_INSERT [dbo].[Import_Details] OFF
GO
SET IDENTITY_INSERT [dbo].[OrderDetail] ON 

INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (202, 150, 11, N'ĐỒNG HỒ CASIO GA-100DE-2ADR NỮ PIN DÂY NHỰA', 1, CAST(4393000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (203, 150, 12, N'ĐỒNG HỒ CASIO LA670WL-1BDF NỮ PIN DÂY DA', 1, CAST(766000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (204, 151, 7, N'ĐỒNG HỒ SEIKO SGEG99P1 NAM PIN DÂY DA', 10, CAST(36840000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1210, 1154, 2, N'ĐỒNG HỒ CASIO MTP-1374L-1AVDF NAM PIN DÂY DA', 2, CAST(3354000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1213, 1155, 2, N'ĐỒNG HỒ CASIO MTP-1374L-1AVDF NAM PIN DÂY DA', 2, CAST(3354000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1216, 1156, 8, N'ĐỒNG HỒ TISSOT T063.907.11.058.00 NAM TỰ ĐỘNG DÂY INOX', 1, CAST(21940000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1217, 1157, 8, N'ĐỒNG HỒ TISSOT T063.907.11.058.00 NAM TỰ ĐỘNG DÂY INOX', 1, CAST(21940000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1218, 1158, 9, N'ĐỒNG HỒ CASIO GA-110GB-1ADR NAM PIN DÂY NHỰA', 1, CAST(10000000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1219, 1159, 4, N'ĐỒNG HỒ LOUIS ERARD 13900AA05.BDC102 NAM PIN DÂY DA', 2, CAST(36390600 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1220, 1160, 11, N'ĐỒNG HỒ CASIO GA-100DE-2ADR NỮ PIN DÂY NHỰA', 2, CAST(8786000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1233, 1166, 8, N'ĐỒNG HỒ TISSOT T063.907.11.058.00 NAM TỰ ĐỘNG DÂY INOX', 1, CAST(21940000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1269, 1185, 2, N'ĐỒNG HỒ CASIO MTP-1374L-1AVDF NAM PIN DÂY DA', 1, CAST(1677000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1280, 1188, 18, N'ĐỒNG HỒ ĐÔI ALEXANDRE CHRISTIE AC8C26-1LK TRẮNG – AC8C26-1MK TRẮNG PIN DÂY INOX', 1, CAST(6080000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1281, 1188, 21, N'ĐỒNG HỒ ĐÔI SUNRISE SG – SL1085.1601 PIN DÂY INOX', 1, CAST(4230000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1282, 1188, 22, N'ĐỒNG HỒ ĐÔI OLYMPIA STAR OPA58012-07MSK TRẮNG – OPA58012-07LSK TRẮNG PIN DÂY INOX', 1, CAST(6955000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1283, 1188, 23, N'ĐỒNG HỒ ĐÔI CITIZEN BD0030-00A – ER0190-00A PIN DÂY DA', 1, CAST(5140000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1335, 1213, 21, N'ĐỒNG HỒ ĐÔI SUNRISE SG – SL1085.1601 PIN DÂY INOX', 2, CAST(8460000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1336, 1213, 45, N'No name', 2, CAST(9048018 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1337, 1213, 46, N'No name', 2, CAST(6246000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1338, 1214, 8, N'ĐỒNG HỒ TISSOT T063.907.11.058.00 NAM TỰ ĐỘNG DÂY INOX', 2, CAST(43880000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1339, 1214, 13, N'ĐỒNG HỒ CITIZEN EX1410-88A NỮ ECO-DRIVE DÂY INOX', 2, CAST(12240000 AS Decimal(18, 0)), 1)
INSERT [dbo].[OrderDetail] ([OrderID_STT], [Order_ID], [Product_ID], [Product_Name], [Product_Quantity], [Into_Money], [Status]) VALUES (1340, 1214, 14, N'ĐỒNG HỒ DANIEL WELLINGTON DW00500001 NỮ PIN DÂY INOX', 2, CAST(8460000 AS Decimal(18, 0)), 1)
SET IDENTITY_INSERT [dbo].[OrderDetail] OFF
GO
SET IDENTITY_INSERT [dbo].[Orders] ON 

INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (150, 7, N'Sơn Nguyễn', N'sonnguyeng2001@gmail.com', N'0936249051  ', N'57/45 lô tư', CAST(N'2022-03-26' AS Date), N'HCM', N'Khong', CAST(5159000 AS Decimal(18, 0)), CAST(1000000 AS Decimal(18, 0)), N'Received', NULL)
INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (151, 7, N'Sơn Nguyễn', N'sonnguyeng2001@gmail.com', N'0936249051  ', N'57/45 lô tư', CAST(N'2022-03-26' AS Date), N'HCM', N'', CAST(36840000 AS Decimal(18, 0)), CAST(0 AS Decimal(18, 0)), N'Received', NULL)
INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (1154, 7, N'Sơn Nguyễn', N'sonnguyeng2001@gmail.com', N'0936249051  ', N'No', CAST(N'2022-04-08' AS Date), N'HCM', N'', CAST(3354000 AS Decimal(18, 0)), CAST(0 AS Decimal(18, 0)), N'Received', NULL)
INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (1155, 8, N'Nguyễn Tấn Toàn', N'sonnguyeng769@gmail.com', N'01695192259 ', N'Tân Bình', CAST(N'2022-04-08' AS Date), N'Hồ Chí Minh', N'', CAST(3354000 AS Decimal(18, 0)), CAST(0 AS Decimal(18, 0)), N'Received', NULL)
INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (1156, NULL, N'Phòng Nghiệp Vụ ', N'12eq@c', N'0936249051  ', N'Q.Tân Phú', CAST(N'2022-04-08' AS Date), N'Hồ Chí Minh', N'', CAST(21940000 AS Decimal(18, 0)), CAST(0 AS Decimal(18, 0)), N'Received', NULL)
INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (1157, NULL, N'Phòng Nghiệp Vụ 1', N'nguyenvandung251210@gmail.com', N'0936249051  ', N'Q.Tân Phú', CAST(N'2022-04-08' AS Date), N'Hồ Chí Minh', N'', CAST(21940000 AS Decimal(18, 0)), CAST(0 AS Decimal(18, 0)), N'Received', NULL)
INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (1158, NULL, N'Sơn Nguyễn', N'sonnguyeng2001@gmail.com', N'0936249051  ', N'Q.Tân Phú', CAST(N'2022-04-08' AS Date), N'Hồ Chí Minh', N'', CAST(10000000 AS Decimal(18, 0)), CAST(0 AS Decimal(18, 0)), N'Received', NULL)
INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (1159, NULL, N'Nguyễn Văn Dũng', N'sonnguyeng2001@gmail.com', N'0936249051  ', N'Q.Tân Phú', CAST(N'2022-04-08' AS Date), N'Hồ Chí Minh', N'', CAST(36390600 AS Decimal(18, 0)), CAST(0 AS Decimal(18, 0)), N'Received', NULL)
INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (1160, NULL, N'Sơn Nguyễn', N'sonnguyeng2001@gmail.com', N'0936249051  ', N'Q.Tân Phú', CAST(N'2022-04-08' AS Date), N'Hồ Chí Minh', N'Khong', CAST(8786000 AS Decimal(18, 0)), CAST(0 AS Decimal(18, 0)), N'Received', NULL)
INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (1166, 7, N'Sơn Nguyễn', N'sonnguyeng2001@gmail.com', N'0936249051  ', N'No', CAST(N'2022-04-08' AS Date), N'HCM', N'', CAST(21940000 AS Decimal(18, 0)), CAST(0 AS Decimal(18, 0)), N'Received', NULL)
INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (1185, 7, N'Sơn Nguyễn', N'sonnguyeng2001@gmail.com', N'0936249051  ', N'No', CAST(N'2022-04-20' AS Date), N'HCM', N'', CAST(1677000 AS Decimal(18, 0)), CAST(0 AS Decimal(18, 0)), N'Received', NULL)
INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (1188, 7, N'Sơn Nguyễn', N'sonnguyeng2001@gmail.com', N'0936249051  ', N'No', CAST(N'2022-04-22' AS Date), N'HCM', N'', CAST(22405000 AS Decimal(18, 0)), CAST(0 AS Decimal(18, 0)), N'Received', NULL)
INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (1213, 7, N'Sơn Nguyễn', N'sonnguyeng2001@gmail.com', N'0936249051  ', N'No', CAST(N'2022-05-07' AS Date), N'HCM', N'', CAST(22754018 AS Decimal(18, 0)), CAST(1000000 AS Decimal(18, 0)), N'Received', 0)
INSERT [dbo].[Orders] ([Order_ID], [UserID], [Name], [Email], [Phone], [Address], [Create_Date], [City], [Note], [Total], [Discount], [Status], [Point]) VALUES (1214, 7, N'Sơn Nguyễn', N'sonnguyeng2001@gmail.com', N'0936249051  ', N'No', CAST(N'2022-05-07' AS Date), N'HCM', N'', CAST(64360000 AS Decimal(18, 0)), CAST(0 AS Decimal(18, 0)), N'Received', 220000)
SET IDENTITY_INSERT [dbo].[Orders] OFF
GO
SET IDENTITY_INSERT [dbo].[Product] ON 

INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (2, N'ĐỒNG HỒ CASIO MTP-1374L-1AVDF NAM PIN DÂY DA', CAST(1677000 AS Decimal(18, 0)), 6, N'Đồng hồ nam CASIO MTP-1374L-1AVDF thay cho thiết kế cửa sổ lich cổ điển là thiết kế mới lịch ngày và thứ đều sử dụng đồng hồ kim mang tính hiện đại, trẻ trung. Nổi bật trên nền mặt số đen là thiết kế phá cách kim giây đỏ làm điểm nhấn nổi bật. Dây đeo bằng da tạo vân cá sấu nổi bật với hai đường chỉ may trắng tinh xảo.', N'Image_Nam_2.jpg', N'Pin (Quartz)', N'Dây Da', N'Kính Cứng', N'Tròn', N'> 44 mm', N'Đen', N'Đi Mưa Nhỏ (3 ATM)', N'Casio ', N'Nhật Bản', 1, 22, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-casio-mtp-1374l-1avdf-nam-pin-day-da-a-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (3, N'ĐỒNG HỒ CITIZEN AU1080-20A NAM ECO-DRIVE DÂY VẢI', CAST(5000000 AS Decimal(18, 0)), 1, N'Đồng hồ nam Citizen AU1080-20A nổi bật Pin sử dụng công nghệ hiện đại Eco-Drive (Năng Lượng Ánh Sáng), với thiết kế theo phong cách thời trang với dây đeo chất liệu bằng vải tông màu kem trẻ trung.', N'Image_Nam_3.jpg', N'Năng Lượng Ánh Sáng', N'Dây Vải', N'Kính Sapphire', N'Tròn', N'40 - 43 mm', N'Trắng', N'Đi Mưa Nhỏ (3 ATM)', N'Citizen', N'Nhật Bản', 2, 2, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-citizen-au1080-20a-nam-eco-drive-day-vai-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (4, N'ĐỒNG HỒ LOUIS ERARD 13900AA05.BDC102 NAM PIN DÂY DA', CAST(18195300 AS Decimal(18, 0)), 5, N'Đây là dòng sản phẩm tuyệt vời cho những người đang tìm kiếm chiếc đồng hồ được thiết kế riêng mang đầy đủ sự “chất” Vintage cho đến hiện nay, đó là “chất cổ điển” và chỉ là “cổ điển” tinh khiết.', N'Image_Nam_4.jpg', N'Pin (Quatrz)', N'Dây Da', N'Kính Sapphire', N'Tròn', N'40 - 43 mm', N'Xanh', N'Đi Tắm ( 5 ATM)', N'Louis Eard', N'Thụy Sĩ', 2, 2, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/13900AA05.BDC102-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (5, N'ĐỒNG HỒ OLYM PIANUS OP99141-71AGSK TRẮNG NAM TỰ ĐỘNG DÂY INOX', CAST(1098000 AS Decimal(18, 0)), 11, N'Mẫu đồng hồ Olym Pianus OP99141-71AGSK vẻ ngoài tinh tế sang trọng ấn tượng với kiểu thiết kế độc đáo đến từ ô chân kính phô diễn ra 1 phần trải nghiệm hoạt động của bộ máy cơ đầy nam tính.', N'Image_Nam_5.jpg', N'Kinetic (Vừa Pin – Vừa Tự Động)', N'Dây Kim Loại', N'Kính Sapphire', N'Tròn', N'40 - 43 mm', N'Bạc, Vàng', N'Đi Tắm ( 5 ATM)', N'Olym Pianus – Olympia Star', N'Nhật Bản', 2, 3, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-olym-pianus-op99141-71agsk-trang-nam-tu-dong-day-inox-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (6, N'ĐỒNG HỒ ORIENT FSTAA002W0 NAM PIN DÂY DA', CAST(2737000 AS Decimal(18, 0)), 15, N'Đồng hồ Orient FSTAA002W0 có vỏ kim loại phủ màu vàng sang trọng, kim chỉ và vạch số thanh mãnh nổi bật trên nền số, ô lịch ngày vị trí 3h tinh tế, dây đeo bằng chất liệu da cao cấp màu nâu đem lại phong cách lịch lãm, sang trọng cho phái mạnh', N'Image_Nam_6.jpg', N'Pin (Quartz)', N'Dây Da', N'Kính Cứng', N'Chữ nhật', N'35 - 39 mm', N'Trắng, Vàng', N'Đi Tắm (5 ATM)', N'Orient', N'Nhật Bản', 2, 2, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/FSTAA002W0-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (7, N'ĐỒNG HỒ SEIKO SGEG99P1 NAM PIN DÂY DA', CAST(3684000 AS Decimal(18, 0)), 7, N'Đồng hồ Seiko SGEG99P1 dành cho nam, mặt đồng hồ màu đen, chữ số La Mã lớn màu trắng, vỏ thép không gỉ, dây da màu đen, mặt kính Sapphire chịu lực chống trầy, 1 ô lịch hiển thị ngày.', N'Image_Nam_7.jpg', N'Pin (Quartz)', N'Dây Da', N'Kính Sapphire', N'Tròn', N'40 - 43 mm', N'Đen', N'Đi Bơi (10 ATM)', N'
Seiko', N'Nhật Bản', 1, 47, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-seiko-sgeg99p1-nam-pin-day-da-a-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (8, N'ĐỒNG HỒ TISSOT T063.907.11.058.00 NAM TỰ ĐỘNG DÂY INOX', CAST(21940000 AS Decimal(18, 0)), 6, N'Giản dị và thanh lịch đến từ mẫu đồng hồ Tissot T063.907.11.058.00, được gia công tạo hình với kiểu dáng mỏng tạo nên vẻ tinh tế đầy sang trọng cùng chi tiết kim chỉ vạch số được bao phủ vàng hồng.', N'Image_Nam_8.jpg', N'Kinetic (Vừa Pin – Vừa Tự Động)', N'Dây Kim Loại', N'Kính Sapphire', N'Tròn', N'40 - 43 mm', N'Đen', N'Chưa biết', N'Tissot', N'Thụy Sĩ', 1, 72, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-tissot-t063.907.11.058.00-nam-tu-dong-day-inox-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (9, N'ĐỒNG HỒ CASIO GA-110GB-1ADR NAM PIN DÂY NHỰA', CAST(10000000 AS Decimal(18, 0)), 9, N'Đồng hồ nam CASIO GA-110GB-1AVDF có thiết kế mới sử dụng kim loại màu vàng làm vạch số và kim nổi bật, sang trọng hơn so với thiết kế cũ nên mẫu GA-110GB-1AVDF rất được lòng giới trẻ hiện nay.', N'Image_Nam_1.jpg', N'Pin (Quartz)', N'Dây Nhựa / Cao Su', N'Kính Cứng', N'Tròn', N'30 - 34 mm', N'Đen, Vàng', N'Đi Tắm (5 ATM)', N'Casio, G-Shock & Baby-G', N'Nhật Bản', 1, 19, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-casio-ga-110gb-1adr-nam-pin-day-nhua-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (10, N'ĐỒNG HỒ CANDINO C4433/3 NỮ PIN DÂY INOX', CAST(3996000 AS Decimal(18, 0)), 10, N'Đồng hồ dây da thời trang nữ Candino C4433/3, với mặt đồng hồ sang trọng nền trắng có ánh xà cừ có đính hạt pha lê viền xung quang, kính Sapphire, chữ số lớn dễ đọc, 3 kim chỉ màu bạc.', N'Image_Nu_9.jpg', N'Pin (Quartz)', N'Dây Kim Loại', N'Kính Sapphire', N'Chữ nhật', N'< 29 mm', N'Đen', N'Đi Mưa Nhỏ (3 ATM)', N'Candino', N'Thụy Sĩ', 2, 0, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-tissot-t41.1.183.34-nu-tu-dong-day-inox-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (11, N'ĐỒNG HỒ CASIO GA-100DE-2ADR NỮ PIN DÂY NHỰA', CAST(4393000 AS Decimal(18, 0)), 12, N'Mẫu G-Shock GA-100DE-2ADR với vẻ ngoài cá tính thích hợp cho những bạn trẻ năng động, phù hợp cho những chuyến đi phượt ấn tượng với khả năng chịu nước lên đến 20ATM, với đồng hồ điện tử hiện thị đa chức năng tiện ích.', N'Image_Nu_2.jpg', N'Pin (Quartz)', N'Dây Nhựa / Cao Su', N'Kính Cứng', N'Tròn', N'> 44 mm', N'Xanh', N'Lặn Biển (20 ATM)', N'G-Shock & Baby-G', N'Nhật Bản', 1, 0, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/EX1410-88A-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (12, N'ĐỒNG HỒ CASIO LA670WL-1BDF NỮ PIN DÂY DA', CAST(766000 AS Decimal(18, 0)), 10, N'Mẫu đồng hồ Casio LA670WL-1BDF  với thiết kế bộ máy nhỏ gọn tạo nên vẻ ngoài thanh mảnh nữ tính, vỏ máy tông màu vàng phối cùng mẫu dây đeo kim loại đen tăng thêm vẻ đẹp thời trang.', N'Image_Nu_3.jpg', N'Pin (Quartz)', N'Dây Da', N'Kính nhựa', N'Vuông', N'< 29 mm', N'Bạc, Đen', N'Đi Mưa Nhỏ (3 ATM)', N'Casio ', N'Nhật Bản', 1, 5, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-ogival-og385-032lw-t-nu-pin-day-inox-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (13, N'ĐỒNG HỒ CITIZEN EX1410-88A NỮ ECO-DRIVE DÂY INOX', CAST(6120000 AS Decimal(18, 0)), 14, N'Đồng hồ Citizen EX1410-88A có mặt số hình chữ nhật bầu tinh tế, kim chỉ và vạch số thanh mãnh nổi bật trên nền số màu trắng trang nhã, phần quai được đính pha lê Swarovski sang trọng mang đến vẻ thanh lịch, duyên dáng dành cho phái nữ.', N'Image_Nu_4.jpg', N'Năng Lượng Ánh Sáng', N'Dây Kim Loại, Dây TiTanium', N'Kính Cứng', N'Đặc biệt', N'< 29 mm', N'Bạc', N'Đi Mưa Nhỏ (3 ATM)', N'Citizen', N'Nhật Bản', 1, 17, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-candino-c4433_3-nu-pin-day-inox-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (14, N'ĐỒNG HỒ DANIEL WELLINGTON DW00500001 NỮ PIN DÂY INOX', CAST(4230000 AS Decimal(18, 0)), 14, N'Mẫu đồng hồ nữ Daniel Wellington DW00500001 với nét đặc trưng giản dị đến từ thương hiệu Daniel Wellington với thiết kế bộ máy nhỏ gọn thanh mảnh kết hợp cùng mẫu dây đeo chất liệu vải mang phong cách trẻ trung.', N'Image_Nu_5.jpg', N'Pin (Quartz)', N'Dây Kim Loại', N'Kính Cứng', N'Tròn', N'30 - 34 mm', N'Đen', N'Đi Mưa Nhỏ (3 ATM)', N'Daniel Wellington (DW)', N'Thụy Điển', 1, 4, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/885sslb-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (15, N'ĐỒNG HỒ OGIVAL OG385-032LW-T NỮ PIN DÂY INOX', CAST(9384000 AS Decimal(18, 0)), 11, N'Vẻ ngoài trẻ trung với phần mặt số được phối tông nền trắng có họa tiết thời trang nam tính với vỏ máy dày dặn chứa đựng một trải nghiệm nam tính từ bộ may cơ là yếu tố tạo nên mẫu đồng hồ nam Ogival', N'Image_Nu_6.jpg', N'Pin (Quartz)', N'Dây Kim Loại', N'Kính Sapphire', N'Tròn', N'35 - 39 mm', N'Trắng', N'Đi Mưa Nhỏ (3 ATM)', N'Ogival', N'Thụy Sĩ', 1, 0, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-daniel-wellington-dw00500001-nu-pin-day-inox-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (16, N'ĐỒNG HỒ SKAGEN 885SSLB NỮ PIN DÂY DA', CAST(5900000 AS Decimal(18, 0)), 10, N'Đồng hồ độc đáo dành cho nữ giới Skagen 885SSLB, với vỏ đồng hồ là thép không gỉ, kiểu dáng xoáy, mặt đồng hồ có trắng, dây da màu đen cao cấp, còn có 2 kim chỉ tinh tế.', N'Image_Nu_7.jpg', N'Pin (Quartz)', N'Dây Da', N'Kính Cứng', N'Đặc biệt', N'< 29 mm', N'Trắng', N'Đi Mưa Nhỏ (3 ATM)', N'Skagen', N'Đan Mạch', 1, 0, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-casio-ga-100de-2adr-nu-pin-day-nhua-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (17, N'ĐỒNG HỒ TISSOT T41.1.183.34 NỮ TỰ ĐỘNG DÂY INOX', CAST(17640000 AS Decimal(18, 0)), 10, N'Mẫu Tissot T41.1.183.34 vẻ ngoài giản dị của chiếc đồng hồ 3 kim nhưng lại khoác lên sự trang nhã với nền mặt số được phối tông màu trắng trước bề mặt kính Sapphire kết hợp cùng tổng thể chiếc đồng hồ kim loại màu bạc đầy sang trọng.', N'Image_Nu_8.jpg', N'Cơ (Automatic)', N'Dây Kim Loại', N'Kính Sapphire', N'Tròn', N'< 29 mm', N'Trắng', N'Đi Mưa Nhỏ (3 ATM)', N'Tissot', N'Thụy Sĩ', 1, 0, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-casio-la670wl-1bdf-nu-pin-day-da-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (18, N'ĐỒNG HỒ ĐÔI ALEXANDRE CHRISTIE AC8C26-1LK TRẮNG – AC8C26-1MK TRẮNG PIN DÂY INOX', CAST(6080000 AS Decimal(18, 0)), 12, N'ALEXANDRE CHRISTIE là thương hiệu đồng hồ chính hãng nổi tiếng của Nhật Bản với những thiết kế cầu kỳ và vô cùng tinh tế. Ngay từ khi ra đời mẫu đồng hồ đeo tay này đã nhanh chóng được mọi người yêu thích vì chất lượng tốt động cơ bền bỉ vô cùng sang trọng.', N'Image_Couple_1.jpg', N'Pin (Quartz)', N'Dây Kim Loại', N'Kính Sapphire', N'Tròn', N'35 - 39 mm', N' Vàng', N'Đi Mưa Nhỏ (3 ATM)', N'Alexandre Christie', N'Thụy Sĩ', 3, 6, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-doi-alexandre-christie-ac8c26-1lk-trang-ac8c26-1mk-trang-pin-day-inox-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (21, N'ĐỒNG HỒ ĐÔI SUNRISE SG – SL1085.1601 PIN DÂY INOX', CAST(4230000 AS Decimal(18, 0)), 2, N'Khi mua cặp đồng hồ đôi Sunrise SG.SL1085.1601, quý khách sẽ được bảo hành toàn cầu 1 năm, ngoài ra quý khách sẽ được tặng gói bảo hành máy và thay pin miễn phí trọn đời tại cửa hàng chúng tôi.', N'Image_Couple_2.jpg', N'Pin (Quartz)', N'Dây Kim Loại', N'Kính Sapphire', N'Tròn', N'30 - 34 mm', N'Đen', N'Đi Mưa Nhỏ (3 ATM)', N'Sunrise', N'Thụy Sĩ', 3, 11, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-doi-sunrise-sg-sl1085.1601-pin-day-inox-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (22, N'ĐỒNG HỒ ĐÔI OLYMPIA STAR OPA58012-07MSK TRẮNG – OPA58012-07LSK TRẮNG PIN DÂY INOX', CAST(6955000 AS Decimal(18, 0)), 13, N'Đồng hồ đôi Olym Pianus (Olympia Star) mặt đồng hồ vàng sang trọng với chất liệu thép không gỉ, dây đeo đờ mi cao cấp, còn có 3 kim chỉ và 1 lịch ngày.', N'Image_Couple_3.jpg', N'Pin (Quartz)', N'Dây Kim Loại', N'Kính Sapphire', N'Tròn', N'30 - 34 mm', N'Trắng', N'Đi Mưa Nhỏ (3 ATM)', N'Olym Pianus – Olympia Star', N'Thụy Sĩ', 3, 14, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-doi-olympia-star-opa58012-07msk-trang-opa58012-07lsk-trang-pin-day-inox-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (23, N'ĐỒNG HỒ ĐÔI CITIZEN BD0030-00A – ER0190-00A PIN DÂY DA', CAST(5140000 AS Decimal(18, 0)), 14, N'Đồng hồ đôi Citizen dây da với mặt đồng hồ chữ nhật lớn có nền trắng có nền trắng, dây da cao cấp màu đen có vân, và 3 kim chỉ cao cấp.', N'Image_Couple_4.jpg', N'Pin (Quartz)', N'Dây Da', N'Kính Cứng', N'Chữ nhật', N'30 - 34 mm', N'Bạc', N'Đi Mưa Nhỏ (3 ATM)', N'Citizen', N'Nhật Bản', 3, 1, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-citizen-bd0030-00a-er0190-00a-doi-pin-day-da-a-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (24, N'ĐỒNG HỒ ĐÔI CASIO MTP-E312D-7BVDF – LTP-E312D-4BVDF PIN DÂY INOX', CAST(4324000 AS Decimal(18, 0)), 10, N'Đồng hồ đôi Casio với phong cách trẻ trung, vạch số được thiết kế mỏng tinh tế kèm theo 3 ô phụ với 3 chức năng tiện ích, vỏ máy cùng với dây đeo kim loại đem lại vẻ chắc chắn bền vững cho cặp đôi.

Số lượng
1
 THÊM VÀO GIỎ', N'Image_Couple_5.jpg', N'Pin (Quartz)', N'Dây Kim Loại', N'Kính Cứng', N'Tròn', N'30 - 34 mm, 40 - 43 mm', N'Hồng, Xám', N'Đi Tắm (5 ATM)', N'Casio ', N'Nhật Bản', 3, 0, N'http://mauweb.monamedia.net/dongho/wp-content/uploads/2018/03/dong-ho-casio-mtp-e312d-7bvdf-ltp-e312d-4bvdf-doi-pin-day-inox-a-600x600-300x300.jpg')
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (41, N'No Name', CAST(10000 AS Decimal(18, 0)), 10, N'No Name', N'Image_Nam_9.jpg', N'No name', N'No name', N'No name', N'No name', N'No name', N'No name', N'No name', N'No name', N'No name', 1, 0, NULL)
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (44, N'Đồng hồ đôi No name', CAST(100 AS Decimal(18, 0)), 10, N'không', N'Tommy_Hilfiger-1710383_1.jpg', N'Pin/Quarts', N'Dây da tổng hợp', N'Kính Sapphire', N'Chữ nhật', N'No name', N'Đen, Vàng', N'No name', N'Rolex ', N'Nhật Bản', 3, 0, NULL)
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (45, N'No name', CAST(4524009 AS Decimal(18, 0)), 9, N'không', N'Tommy_Hilfiger-1791348_2.jpg', N'Pin/Quarts', N'Chất liệu dây', N'Kính Cứng', N'No name', N'< 29 mm', N'Trắng', N'Chưa biết', N'Citizen', N'Thụy Sĩ', 2, 3, NULL)
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (46, N'No name', CAST(3123000 AS Decimal(18, 0)), 9, N'không', N'Tommy_Hilfiger-1791424_3.jpg', N'Năng Lượng Ánh Sáng', N'Chất liệu dây', N'Kính Cứng', N'Mặt tròn', N'40mm', N'Vàng', N'Chưa biết', N'Citizen', N'No name', 2, 2, NULL)
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (47, N'Casio MTP-VT01GL-2B', CAST(85403500 AS Decimal(18, 0)), 10, N'không', N'Tommy_Hilfiger-1791580_4.jpg', N'Pin/Quarts', N'Chất liệu dây', N'Kính Cứng', N'Chữ nhật', N'< 29 mm', N'Vàng', N'Chưa biết', N'Casio', N'Xuất xứ', 2, 7, NULL)
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (48, N'Đồng hồ Rolex Datejust 278278 Mặt Số Butterfly', CAST(4235000 AS Decimal(18, 0)), 10, N'không', N'Tommy_Hilfiger-1791529_5.jpg', N'No name', N'No name', N'No name', N'Mặt tròn', N'35 - 39 mm', N'Vàng', N'Chưa biết', N'Citizen', N'No name', 2, 0, NULL)
INSERT [dbo].[Product] ([Product_ID], [Product_Name], [Price], [Quantity], [Description], [Image], [Aparatus and Energy], [Material_Day], [Material_Matkinh], [Dial_HinhDang], [Dial_KichThuoc], [Dial_MauSac], [Waterproof], [TradeMark], [Origin], [Category_ID], [Sales], [ImageLink]) VALUES (49, N'ĐỒNG HỒ TISSOT T41.1.183.34 NỮ TỰ ĐỘNG DÂY INOX ', CAST(65469700 AS Decimal(18, 0)), 10, N'không', N'Tommy_Hilfiger-1791580_6.jpg', N'Pin (Quartz)', N'Chất liệu dây', N'Chất liệu mặt kính', N'Đặc biệt', N'30 - 34 mm', N'Đen, Vàng', N'Chưa biết', N'Citizen', N'No name', 1, 2, NULL)
SET IDENTITY_INSERT [dbo].[Product] OFF
GO
SET IDENTITY_INSERT [dbo].[Providerr] ON 

INSERT [dbo].[Providerr] ([Provider_ID], [Provider_Name]) VALUES (1, N'Nhà cung cấp 1')
INSERT [dbo].[Providerr] ([Provider_ID], [Provider_Name]) VALUES (2, N'Nhà cung cấp 2')
INSERT [dbo].[Providerr] ([Provider_ID], [Provider_Name]) VALUES (3, N'Nhà cung cấp 3')
INSERT [dbo].[Providerr] ([Provider_ID], [Provider_Name]) VALUES (4, N'Nhà cung cấp 4')
SET IDENTITY_INSERT [dbo].[Providerr] OFF
GO
SET IDENTITY_INSERT [dbo].[Users] ON 

INSERT [dbo].[Users] ([UserID], [Username], [Password], [Permission], [CustomerName], [CustomerEmail], [CustomerPhone], [CustomerAddress], [CustomerCity], [CustomerToken], [RewardPoints]) VALUES (1, N'admin', N'admin', 1, NULL, NULL, NULL, NULL, NULL, NULL, 10)
INSERT [dbo].[Users] ([UserID], [Username], [Password], [Permission], [CustomerName], [CustomerEmail], [CustomerPhone], [CustomerAddress], [CustomerCity], [CustomerToken], [RewardPoints]) VALUES (7, N'user1', N'123', 0, N'Sơn Nguyễn', N'sonnguyeng2001@gmail.com', N'0936249051  ', N'No', N'HCM', N'Q19T2M17', 0)
INSERT [dbo].[Users] ([UserID], [Username], [Password], [Permission], [CustomerName], [CustomerEmail], [CustomerPhone], [CustomerAddress], [CustomerCity], [CustomerToken], [RewardPoints]) VALUES (8, N'user2', N'123', 0, N'Nguyễn Tấn Toàn', N'sonnguyeng769@gmail.com', N'01695192259 ', N'Tân Bình', N'Hồ Chí Minh', NULL, 51)
INSERT [dbo].[Users] ([UserID], [Username], [Password], [Permission], [CustomerName], [CustomerEmail], [CustomerPhone], [CustomerAddress], [CustomerCity], [CustomerToken], [RewardPoints]) VALUES (9, N'nguyenvandung251210@gmail.com', N'123', 0, N'Nguyễn Văn Dũng', N'nguyenvandung251210@gmail.com', N'0908420536  ', N'Tân Phú', N'Hồ Chí Minh', N'NZKALM2E', 10)
SET IDENTITY_INSERT [dbo].[Users] OFF
GO
ALTER TABLE [dbo].[Customer_Product]  WITH CHECK ADD  CONSTRAINT [FK_Customer_Product_Product] FOREIGN KEY([Product_ID])
REFERENCES [dbo].[Product] ([Product_ID])
ON UPDATE CASCADE
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[Customer_Product] CHECK CONSTRAINT [FK_Customer_Product_Product]
GO
ALTER TABLE [dbo].[Customer_Product]  WITH CHECK ADD  CONSTRAINT [FK_Customer_Product_Users] FOREIGN KEY([Customer_ID])
REFERENCES [dbo].[Users] ([UserID])
ON UPDATE CASCADE
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[Customer_Product] CHECK CONSTRAINT [FK_Customer_Product_Users]
GO
ALTER TABLE [dbo].[FeedBack]  WITH CHECK ADD  CONSTRAINT [FK_FeedBack_Product] FOREIGN KEY([Product_ID])
REFERENCES [dbo].[Product] ([Product_ID])
GO
ALTER TABLE [dbo].[FeedBack] CHECK CONSTRAINT [FK_FeedBack_Product]
GO
ALTER TABLE [dbo].[Import]  WITH CHECK ADD  CONSTRAINT [FK_Import_Providerr] FOREIGN KEY([Provider_ID])
REFERENCES [dbo].[Providerr] ([Provider_ID])
GO
ALTER TABLE [dbo].[Import] CHECK CONSTRAINT [FK_Import_Providerr]
GO
ALTER TABLE [dbo].[Import_Details]  WITH CHECK ADD  CONSTRAINT [FK_Import_Details_Import] FOREIGN KEY([Import_ID])
REFERENCES [dbo].[Import] ([Import_ID])
GO
ALTER TABLE [dbo].[Import_Details] CHECK CONSTRAINT [FK_Import_Details_Import]
GO
ALTER TABLE [dbo].[Import_Details]  WITH CHECK ADD  CONSTRAINT [FK_Import_Details_Product] FOREIGN KEY([Product_ID])
REFERENCES [dbo].[Product] ([Product_ID])
GO
ALTER TABLE [dbo].[Import_Details] CHECK CONSTRAINT [FK_Import_Details_Product]
GO
ALTER TABLE [dbo].[OrderDetail]  WITH CHECK ADD  CONSTRAINT [fk_od_pro] FOREIGN KEY([Product_ID])
REFERENCES [dbo].[Product] ([Product_ID])
ON UPDATE CASCADE
GO
ALTER TABLE [dbo].[OrderDetail] CHECK CONSTRAINT [fk_od_pro]
GO
ALTER TABLE [dbo].[OrderDetail]  WITH CHECK ADD  CONSTRAINT [FK_OrderDetail_Orders] FOREIGN KEY([Order_ID])
REFERENCES [dbo].[Orders] ([Order_ID])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[OrderDetail] CHECK CONSTRAINT [FK_OrderDetail_Orders]
GO
ALTER TABLE [dbo].[Orders]  WITH CHECK ADD  CONSTRAINT [FK_Orders_Users] FOREIGN KEY([UserID])
REFERENCES [dbo].[Users] ([UserID])
GO
ALTER TABLE [dbo].[Orders] CHECK CONSTRAINT [FK_Orders_Users]
GO
ALTER TABLE [dbo].[Product]  WITH CHECK ADD  CONSTRAINT [fk_pro_cate] FOREIGN KEY([Category_ID])
REFERENCES [dbo].[Category] ([Category_ID])
GO
ALTER TABLE [dbo].[Product] CHECK CONSTRAINT [fk_pro_cate]
GO
