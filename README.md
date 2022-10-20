# Database_clinic_system
-- phpMyAdmin SQL Dump
-- version 5.2.0
-- https://www.phpmyadmin.net/
--
-- Host: 127.0.0.1
-- Generation Time: Jul 04, 2022 at 09:58 AM
-- Server version: 10.4.24-MariaDB
-- PHP Version: 8.1.6

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Database: `scp_database_system`
--

-- --------------------------------------------------------

--
-- Table structure for table `customer`
--

CREATE TABLE `customer` (
  `CustomerID` int(11) NOT NULL,
  `CustomerName` varchar(100) DEFAULT NULL,
  `CustomerproductID` int(11) DEFAULT NULL,
  `CustomerPrice` int(11) DEFAULT NULL,
  `CustomerLocation` varchar(100) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Table structure for table `master_customer`
--

CREATE TABLE `master_customer` (
  `CustomerID` int(11) NOT NULL,
  `CustomerName` varchar(100) DEFAULT NULL,
  `CustomerproductID` int(11) DEFAULT NULL,
  `PaymentID` int(11) DEFAULT NULL,
  `SupplierID` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `master_customer`
--

INSERT INTO `master_customer` (`CustomerID`, `CustomerName`, `CustomerproductID`, `PaymentID`, `SupplierID`) VALUES
(112, 'MAMAT', 0, 914, 898911),
(114, 'MAMAT', 0, 9100, 898908),
(1113, 'ALI', 0, 901, 898912);

-- --------------------------------------------------------

--
-- Table structure for table `master_payment`
--

CREATE TABLE `master_payment` (
  `PaymentID` int(11) NOT NULL,
  `PaymentPrice` int(11) DEFAULT NULL,
  `Paymentdate` date DEFAULT NULL,
  `PaymentDesc` varchar(300) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Table structure for table `master_product`
--

CREATE TABLE `master_product` (
  `ProductID` int(11) NOT NULL,
  `ProductName` varchar(300) DEFAULT NULL,
  `ProductType` varchar(20) DEFAULT NULL,
  `ProductQTY` int(11) DEFAULT NULL,
  `ProductPrice` int(11) DEFAULT NULL,
  `locationID` int(11) DEFAULT NULL,
  `CustomerID` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `master_product`
--

INSERT INTO `master_product` (`ProductID`, `ProductName`, `ProductType`, `ProductQTY`, `ProductPrice`, `locationID`, `CustomerID`) VALUES
(1, 'Ayam Gred A', 'Ayam ', 40, 20, 901, 101),
(2, 'Ayam Gred B', 'Ayam ', 60, 15, 902, 102),
(3, 'Ayam Gred C', 'Ayam ', 100, 12, 903, 103),
(4, 'Ayam Gred D', 'Ayam ', 110, 10, 904, 104),
(5, 'Ayam Gred E', 'Ayam ', 150, 9, 905, 105),
(6, 'Ayam Frozen', 'Ayam ', 40, 12, 906, 106),
(7, 'Telur Gred A', 'Telur', 100, 12, 907, 107),
(8, 'Telur Gred B', 'Telur', 200, 12, 908, 108),
(9, 'Telur Gred C', 'Telur', 250, 12, 909, 109),
(10, 'Telur Gred D', 'Telur', 300, 12, 910, 110),
(11, 'Telur Gred E', 'Telur', 400, 12, 911, 111);

-- --------------------------------------------------------

--
-- Table structure for table `master_staff`
--

CREATE TABLE `master_staff` (
  `StaffID` int(11) NOT NULL,
  `StaffName` varchar(100) DEFAULT NULL,
  `StaffAddress` varchar(300) DEFAULT NULL,
  `Staffdepartment` varchar(20) DEFAULT NULL,
  `locationID` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Table structure for table `master_supplier`
--

CREATE TABLE `master_supplier` (
  `SupplierID` int(11) NOT NULL,
  `SupplierName` varchar(100) DEFAULT NULL,
  `supplierPrice` int(11) DEFAULT NULL,
  `SupplierproductID` int(11) DEFAULT NULL,
  `SupplierLocation` varchar(100) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Table structure for table `payment`
--

CREATE TABLE `payment` (
  `PaymentID` int(11) NOT NULL,
  `PaymentPrice` int(11) DEFAULT NULL,
  `Paymentdate` date DEFAULT NULL,
  `PaymentDesc` varchar(300) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Table structure for table `product_location`
--

CREATE TABLE `product_location` (
  `LocationID` int(11) NOT NULL,
  `LocationName` varchar(100) DEFAULT NULL,
  `LocationAddress` varchar(300) DEFAULT NULL,
  `Locationcity` varchar(100) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Table structure for table `staff`
--

CREATE TABLE `staff` (
  `StaffID` int(11) NOT NULL,
  `StaffName` varchar(100) DEFAULT NULL,
  `StaffAddress` varchar(300) DEFAULT NULL,
  `Staffdepartment` varchar(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Table structure for table `supplier`
--

CREATE TABLE `supplier` (
  `SupplierID` int(11) NOT NULL,
  `SupplierName` varchar(100) DEFAULT NULL,
  `SupplierproductID` int(11) DEFAULT NULL,
  `SupplierPrice` int(11) DEFAULT NULL,
  `SupplierLocation` varchar(100) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Indexes for dumped tables
--

--
-- Indexes for table `customer`
--
ALTER TABLE `customer`
  ADD KEY `CustomerID` (`CustomerID`);

--
-- Indexes for table `master_customer`
--
ALTER TABLE `master_customer`
  ADD PRIMARY KEY (`CustomerID`),
  ADD KEY `PaymentID` (`PaymentID`),
  ADD KEY `SupplierID` (`SupplierID`);

--
-- Indexes for table `master_payment`
--
ALTER TABLE `master_payment`
  ADD PRIMARY KEY (`PaymentID`);

--
-- Indexes for table `master_product`
--
ALTER TABLE `master_product`
  ADD PRIMARY KEY (`ProductID`),
  ADD KEY `locationID` (`locationID`),
  ADD KEY `CustomerID` (`CustomerID`);

--
-- Indexes for table `master_staff`
--
ALTER TABLE `master_staff`
  ADD PRIMARY KEY (`StaffID`),
  ADD KEY `locationID` (`locationID`);

--
-- Indexes for table `master_supplier`
--
ALTER TABLE `master_supplier`
  ADD PRIMARY KEY (`SupplierID`);

--
-- Indexes for table `payment`
--
ALTER TABLE `payment`
  ADD KEY `PaymentID` (`PaymentID`);

--
-- Indexes for table `product_location`
--
ALTER TABLE `product_location`
  ADD PRIMARY KEY (`LocationID`);

--
-- Indexes for table `staff`
--
ALTER TABLE `staff`
  ADD KEY `StaffID` (`StaffID`);

--
-- Indexes for table `supplier`
--
ALTER TABLE `supplier`
  ADD KEY `SupplierID` (`SupplierID`);

--
-- Constraints for dumped tables
--

--
-- Constraints for table `customer`
--
ALTER TABLE `customer`
  ADD CONSTRAINT `customer_ibfk_1` FOREIGN KEY (`CustomerID`) REFERENCES `master_customer` (`CustomerID`);

--
-- Constraints for table `master_customer`
--
ALTER TABLE `master_customer`
  ADD CONSTRAINT `master_customer_ibfk_1` FOREIGN KEY (`PaymentID`) REFERENCES `master_payment` (`PaymentID`),
  ADD CONSTRAINT `master_customer_ibfk_2` FOREIGN KEY (`SupplierID`) REFERENCES `master_supplier` (`SupplierID`);

--
-- Constraints for table `master_product`
--
ALTER TABLE `master_product`
  ADD CONSTRAINT `master_product_ibfk_1` FOREIGN KEY (`locationID`) REFERENCES `product_location` (`LocationID`),
  ADD CONSTRAINT `master_product_ibfk_2` FOREIGN KEY (`CustomerID`) REFERENCES `master_customer` (`CustomerID`);

--
-- Constraints for table `master_staff`
--
ALTER TABLE `master_staff`
  ADD CONSTRAINT `master_staff_ibfk_1` FOREIGN KEY (`locationID`) REFERENCES `product_location` (`LocationID`);

--
-- Constraints for table `payment`
--
ALTER TABLE `payment`
  ADD CONSTRAINT `payment_ibfk_1` FOREIGN KEY (`PaymentID`) REFERENCES `master_payment` (`PaymentID`);

--
-- Constraints for table `staff`
--
ALTER TABLE `staff`
  ADD CONSTRAINT `staff_ibfk_1` FOREIGN KEY (`StaffID`) REFERENCES `master_staff` (`StaffID`);

--
-- Constraints for table `supplier`
--
ALTER TABLE `supplier`
  ADD CONSTRAINT `supplier_ibfk_1` FOREIGN KEY (`SupplierID`) REFERENCES `master_supplier` (`SupplierID`);
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
